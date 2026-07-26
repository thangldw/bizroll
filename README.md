# BizRoll production artifact

Repo này chỉ chứa website đã build và được phục vụ tại [thangldw.github.io/bizroll](https://thangldw.github.io/bizroll/).

Mã nguồn, Supabase migrations, test và quy trình phát hành nằm tại [thangldw/bizroll-game](https://github.com/thangldw/bizroll-game).

Không sửa thủ công `index.html` hoặc file trong `assets/`. Mỗi bản phát hành phải được tạo từ `dist/` của source repo sau khi `npm run release:check` đạt.
