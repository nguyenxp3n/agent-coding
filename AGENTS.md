# AGENTS.md

Behavioral guidelines to reduce common LLM coding mistakes. Merge with project-specific instructions as needed.

**Tradeoff:** These guidelines bias toward caution over speed. For trivial tasks, use judgment.

## 1. Think Before Coding

**Don't assume. Don't hide confusion. Surface tradeoffs.**

Before implementing:
- State your assumptions explicitly. If uncertain, ask.
- If multiple interpretations exist, present them - don't pick silently.
- If a simpler approach exists, say so. Push back when warranted.
- If something is unclear, stop. Name what's confusing. Ask.

## 2. Simplicity First

**Minimum code that solves the problem. Nothing speculative.**

- No features beyond what was asked.
- No abstractions for single-use code.
- No "flexibility" or "configurability" that wasn't requested.
- No error handling for impossible scenarios.
- If you write 200 lines and it could be 50, rewrite it.

Ask yourself: "Would a senior engineer say this is overcomplicated?" If yes, simplify.

## 3. Surgical Changes

**Touch only what you must. Clean up only your own mess.**

When editing existing code:
- Don't "improve" adjacent code, comments, or formatting.
- Don't refactor things that aren't broken.
- Match existing style, even if you'd do it differently.
- If you notice unrelated dead code, mention it - don't delete it.

When your changes create orphans:
- Remove imports/variables/functions that YOUR changes made unused.
- Don't remove pre-existing dead code unless asked.

The test: Every changed line should trace directly to the user's request.

## 4. Goal-Driven Execution

**Define success criteria. Loop until verified.**

Transform tasks into verifiable goals:
- "Add validation" → "Write tests for invalid inputs, then make them pass"
- "Fix the bug" → "Write a test that reproduces it, then make it pass"
- "Refactor X" → "Ensure tests pass before and after"

For multi-step tasks, state a brief plan:
```
1. [Step] → verify: [check]
2. [Step] → verify: [check]
3. [Step] → verify: [check]
```

Strong success criteria let you loop independently. Weak criteria ("make it work") require constant clarification.

---

**These guidelines are working if:** fewer unnecessary changes in diffs, fewer rewrites due to overcomplication, and clarifying questions come before implementation rather than after mistakes.

## 5. Quy chuẩn kiến trúc & Điều phối Hệ thống (`./rules/`, `./skills/`, `./agents/`)

Khi làm việc trong dự án này, bạn bắt buộc phải tuân thủ hệ thống quy chuẩn phân tầng sau:

### A. Ràng buộc & Tiêu chuẩn Code (`./rules/`)
Trước khi đọc, sửa hoặc tạo bất kỳ file nào, bạn PHẢI tuân thủ nghiêm ngặt:
- **Coding Style & Patterns**: Tuân thủ `./rules/core/coding-style.md` và `./rules/core/patterns.md`.
- **Quản lý tạo file**: Tuân thủ `./rules/core/file-creation.md` (tuyệt đối không tự ý đẻ file, thư mục hoặc boilerplate suy đoán).
- **Quy trình tuần tự**: Thực thi theo `./rules/core/linear-workflow.md` (làm từng bước có kiểm chứng, không nhảy cóc).
- **Đồng bộ tài liệu**: Đọc `./rules/docs/living-docs.md` để luôn cập nhật tài liệu tương ứng với diff code.
- **Quy chuẩn Tech-Stack**: Áp dụng `./rules/react/` và `./rules/typescript/` cho các file giao diện và logic TypeScript.

### B. Kỹ năng thực thi kích hoạt theo nhu cầu (`./skills/`)

Agent PHẢI kích hoạt đúng quy trình trong `./skills/<tên-skill>/SKILL.md` tùy theo giai đoạn công việc:

1. **Khảo sát & Chuẩn bị (Onboarding & Budgeting):**
   - `./skills/codebase-onboarding/SKILL.md`: Khảo sát, đọc hiểu kiến trúc và luồng dữ liệu của repository mới.
   - `./skills/context-budget/SKILL.md`: Kiểm soát chặt chẽ ngân sách token, cấm nạp file lớn toàn bộ nếu chỉ cần sửa cục bộ.

2. **Làm rõ yêu cầu & Lập kế hoạch (Ideation & Planning):**
   - `./skills/brainstorm/SKILL.md`: Đặt câu hỏi làm rõ các điểm mơ hồ trước khi bắt đầu.
   - `./skills/interview-me/SKILL.md`: Chủ động phỏng vấn người dùng để đào sâu business requirement.
   - `./skills/planning/SKILL.md`: Chia nhỏ bài toán phức tạp thành checklist các bước thực thi độc lập.
   - `./skills/prototype/SKILL.md`: Tạo bản dựng nhanh (PoC/prototype) để kiểm chứng ý tưởng trước khi code thật.

3. **Thiết kế & Giao diện (Frontend Design):**
   - `./skills/frontend-design-bar/`: Cẩm nang thiết kế UI/UX chất lượng cao (tham chiếu các file recipes trong `references/` về layout, color, motion).

4. **Tài liệu & Tri thức (Documentation & Knowledge):**
   - `./skills/log-wiki/SKILL.md`: Ghi chép nhật ký phát triển, kiến thức và quyết định kỹ thuật vào wiki dự án.
   - `./skills/docs-drift/SKILL.md`: Kiểm tra và ngăn chặn tình trạng tài liệu bị lỗi thời so với code thực tế.
   - `./skills/explain/SKILL.md`: Trình bày lý do chọn giải pháp, rủi ro và các đánh đổi (tradeoffs).
   - `./skills/hand-off/SKILL.md`: Đóng gói tóm tắt trạng thái công việc khi chuyển giao session hoặc kết thúc ca làm việc.

5. **Bộ kỹ năng Rà soát & Đánh giá (Review Skills):**
   - `./skills/review/SKILL.md`: Quy trình tự review mã nguồn tổng quát.
   - `./skills/review-change/SKILL.md`: Soi xét từng diff thay đổi để tránh sửa lan man ngoài scope.
   - `./skills/review-experience/SKILL.md`: Đánh giá trải nghiệm người dùng (UX) và độ mượt của luồng tương tác.
   - `./skills/review-health/SKILL.md`: Kiểm tra sức khỏe tổng thể của codebase (tech debt, độ phức tạp, rác).
   - `./skills/review-release/SKILL.md`: Rà soát tiêu chí sẵn sàng trước khi deploy/release.
   - `./skills/security-review/SKILL.md`: Quét các lỗ hổng bảo mật và rò rỉ credential/thông tin nhạy cảm.

### C. Đóng vai các Reviewer chuyên biệt (`./agents/`)
Khi được yêu cầu review, kiểm tra hoặc trước khi chốt code, hãy áp dụng nhân cách (persona) tương ứng:
- **Lập kế hoạch & Kiến trúc**: `./agents/analyst.md`, `./agents/planner.md`, `./agents/architect.md`, `./agents/plan-reviewer.md`.
- **Review chất lượng code**: `./agents/react-reviewer.md`, `./agents/typescript-reviewer.md`, `./agents/database-reviewer.md`.
- **Bảo mật & Săn lỗi ngầm**:
  - Dùng `./agents/silent-failure-hunter.md` để truy bắt `try/catch` nuốt lỗi ngầm và promise hở.
  - Dùng `./agents/security-reviewer.md` để quét lỗ hổng bảo mật.
  - Dùng `./agents/performance-optimizer.md` để tối ưu hiệu năng.
  - Dùng `./agents/refactor-cleaner.md` để dọn dẹp biến thừa/dead-code.