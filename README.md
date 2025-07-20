 Trình Chỉnh Sửa Biểu Đồ UML Trên Desktop Với Rendering Thời Gian Thực

## Tổng Quan Dự Án

**UmlApp** là một ứng dụng desktop hiện đại, trực quan được thiết kế để đơn giản hóa quá trình tạo và chỉnh sửa biểu đồ UML. Nhằm khắc phục những hạn chế của các công cụ UML truyền thống về trải nghiệm người dùng và tính linh hoạt, dự án này tận dụng sức mạnh của **Tauri** (sử dụng Rust) để cung cấp hiệu suất và khả năng tích hợp gốc trên desktop, kết hợp với **React.js (TypeScript)** cho một giao diện người dùng động và phản hồi.

Điểm nổi bật của hệ thống là khả năng rendering biểu đồ UML theo thời gian thực từ cú pháp PlantUML, mang đến phản hồi tức thì cho người dùng. Ứng dụng cũng cung cấp các tính năng quản lý dự án và danh mục hiệu quả, giúp người dùng dễ dàng tổ chức và truy cập các thiết kế của mình.

## ✨ Các Tính Năng Chính

*   **Chỉnh Sửa PlantUML Trực Quan:**
    *   Trình soạn thảo mã tích hợp dựa trên CodeMirror, cung cấp khả năng làm nổi bật cú pháp và tự động hoàn thành cho PlantUML.
    *   Trải nghiệm gõ mã mượt mà và hiệu quả.
*   **Rendering Biểu Đồ Thời Gian Thực:**
    *   Biểu đồ UML được hiển thị tức thì khi bạn gõ mã, cho phép xem trước và điều chỉnh thiết kế ngay lập tức.
    *   Tăng cường hiệu quả quy trình làm việc và giảm thiểu lỗi.
*   **Quản Lý Dự Án & Danh Mục Mạnh Mẽ:**
    *   Tổ chức các biểu đồ UML của bạn vào các dự án và danh mục có cấu trúc.
    *   Các tính năng tạo, chỉnh sửa, đổi tên, và xóa danh mục/dự án.
*   **Kéo & Thả (Drag & Drop) Trực Quan:**
    *   Sắp xếp lại các danh mục và biểu đồ một cách dễ dàng thông qua giao diện kéo và thả tiện lợi.
    *   Cải thiện khả năng sắp xếp và quản lý nội dung.
*   **Lưu Trữ Dữ Liệu Cục Bộ An Toàn:**
    *   Tất cả dữ liệu dự án, danh mục và biểu đồ được lưu trữ an toàn trên thiết bị của bạn.
    *   Đảm bảo quyền riêng tư và khả năng truy cập ngoại tuyến liền mạch.
*   **Giao Diện Người Dùng Hiện Đại & Phản Hồi:**
    *   Được xây dựng với React và các thành phần UI tiên tiến (ví dụ: Shadcn UI), mang lại trải nghiệm người dùng mượt mà và chuyên nghiệp.
    *   Thiết kế linh hoạt và dễ sử dụng.
*   **Ứng Dụng Desktop Đa Nền Tảng:**
    *   Sử dụng Tauri để đóng gói ứng dụng web thành một ứng dụng desktop nhẹ và hiệu quả.
    *   Hỗ trợ hoạt động trên Windows, macOS và Linux.

## 🛠 Ngăn Xếp Công Nghệ

Dự án này được xây dựng dựa trên một bộ công nghệ hiện đại và mạnh mẽ:

*   **Frontend:**
    *   **React.js (với TypeScript):** Thư viện JavaScript để xây dựng giao diện người dùng động và tương tác.
    *   **Vite:** Công cụ build nhanh cho các dự án web hiện đại.
    *   **PNPM:** Trình quản lý gói nhanh và hiệu quả.
    *   **Shadcn UI (và các thành phần UI khác):** Hệ thống thiết kế hiện đại cho các thành phần UI có thể tái sử dụng.
    *   **CodeMirror:** Trình soạn thảo mã nguồn tích hợp cho PlantUML với làm nổi bật cú pháp và hoàn thành.
    *   **Zustand (hoặc tương tự):** (Suy ra từ thư mục `stores`) Quản lý trạng thái cho ứng dụng React.
*   **Desktop Framework:**
    *   **Tauri (với Rust):** Framework để xây dựng ứng dụng desktop đa nền tảng bằng các công nghệ web, cung cấp quyền truy cập vào các API hệ thống gốc.
    *   **Rust:** Ngôn ngữ lập trình hệ thống, cung cấp hiệu suất và an toàn cho lớp nền tảng của Tauri.
*   **Lưu Trữ Dữ Liệu:**
    *   **SQLite (hoặc cơ sở dữ liệu nhúng tương tự):** (Suy ra từ thư mục `databases`) Cơ sở dữ liệu cục bộ, nhẹ, được sử dụng để lưu trữ dự án, danh mục và dữ liệu biểu đồ.
*   **Công Cụ & Tiện Ích:**
    *   **Node.js:** Môi trường thời gian chạy cho các script (ví dụ: `scripts/generate-changelog.js`).
    *   **GitHub Actions:** (Từ `.github/workflows/`) Tự động hóa CI/CD (Tích hợp liên tục/Triển khai liên tục) cho quá trình build và release.

## 🏗 Kiến Trúc

Hệ thống tuân theo mô hình **Frontend + Native Wrapper**, nơi giao diện người dùng web được đóng gói và chạy như một ứng dụng gốc:

1.  **Client (Frontend):**
    *   Được phát triển bằng React.js và TypeScript, chịu trách nhiệm hiển thị giao diện người dùng, thu thập dữ liệu người dùng, và quản lý logic phía client.
    *   Giao tiếp với lớp Tauri để truy cập các tính năng gốc của hệ điều hành.
2.  **Native Wrapper (Tauri/Rust):**
    *   Được xây dựng với Rust và Tauri, đây là lớp "hạt nhân" của ứng dụng desktop.
    *   Tạo cửa sổ ứng dụng, nhúng và phục vụ giao diện người dùng web (các tệp HTML, CSS, JS đã được build).
    *   Cung cấp quyền truy cập an toàn vào các API hệ thống (như hệ thống tệp, quản lý cửa sổ, v.v.).
    *   Có thể xử lý việc rendering PlantUML bằng cách gọi một binary PlantUML cục bộ hoặc tương tác với một dịch vụ rendering.
3.  **Lưu Trữ Dữ Liệu Cục Bộ:**
    *   Dữ liệu của ứng dụng (dự án, danh mục, nội dung biểu đồ) được quản lý và lưu trữ cục bộ bằng một cơ sở dữ liệu nhúng (như SQLite), được truy cập thông qua các API của Tauri.
    *   Điều này đảm bảo hiệu suất cao và khả năng làm việc ngoại tuyến.

## 📂 Cấu Trúc Dự Án

```
Voting-system/ (Lưu ý: Thư mục gốc nên là uml-app/, đây là lỗi copy-paste từ template)
└── uml-app/
    ├── README.md
    ├── CHANGELOG.md
    ├── components.json           # Cấu hình UI components (vd: Shadcn UI)
    ├── index.html                # Điểm vào chính của frontend web
    ├── LICENSE
    ├── package.json              # Dependencies và scripts của frontend
    ├── pnpm-lock.yaml            # Lock file của pnpm
    ├── tsconfig.json             # Cấu hình TypeScript
    ├── tsconfig.node.json
    ├── vite.config.ts            # Cấu hình Vite build
    ├── .env.example              # Mẫu biến môi trường
    ├── .version-lock             # Quản lý khóa phiên bản
    ├── scripts/                  # Các script tiện ích (vd: generate changelog, update tauri pubkey)
    │   ├── generate-changelog.js
    │   ├── update-tauri-pubkey.js
    │   └── version-upgrade.js
    ├── src/                      # Mã nguồn frontend (React TypeScript)
    │   ├── App.css
    │   ├── App.tsx               # Component chính của ứng dụng
    │   ├── main.tsx              # Khởi tạo React
    │   ├── vite-env.d.ts
    │   ├── components/           # Các component UI chung
    │   │   ├── ...
    │   │   └── ui/               # Các component UI cơ bản (ví dụ: từ Shadcn UI)
    │   │       ├── badge.tsx
    │   │       ├── button.tsx
    │   │       └── ...
    │   ├── databases/            # Định nghĩa schema và tương tác với DB cục bộ
    │   │   ├── _db.ts
    │   │   ├── _migrations.ts
    │   │   └── ...
    │   ├── features/             # Các module tính năng lớn (ví dụ: Category, Diagram, Dnd)
    │   │   ├── Category/
    │   │   ├── CategoryDnd/
    │   │   ├── Diagram/
    │   │   ├── DiagramDnd/
    │   │   └── TestSection/
    │   ├── hooks/                # Các React hooks tùy chỉnh
    │   │   ├── useBackground.ts
    │   │   └── useUMLDiagram.ts
    │   ├── lib/                  # Các thư viện tiện ích và cấu hình CodeMirror
    │   │   ├── cache-route.ts
    │   │   └── codemirror/
    │   │       ├── plantuml-completion.ts
    │   │       ├── plantuml.ts
    │   │       └── theme.ts
    │   ├── pages/                # Các trang/view chính của ứng dụng
    │   │   ├── Empty.tsx
    │   │   ├── Home.tsx
    │   │   ├── Preview.tsx
    │   │   ├── Test.tsx
    │   │   └── UMLEditor.tsx
    │   └── stores/               # Quản lý trạng thái (ví dụ: Zustand stores)
    │       ├── category.ts
    │       ├── contentCategory.ts
    │       └── project.ts
    ├── src-tauri/                # Mã nguồn Tauri (Rust)
    │   ├── build.rs
    │   ├── Cargo.toml            # Dependencies và cấu hình Rust
    │   ├── tauri.conf.json       # Cấu hình chính của Tauri
    │   ├── capabilities/         # Định nghĩa quyền hạn của Tauri
    │   │   ├── default.json
    │   │   └── preview-window.json
    │   ├── gen/                  # Tệp được tạo tự động cho các nền tảng cụ thể (ví dụ: Apple)
    │   │   └── apple/
    │   │       └── ...
    │   ├── icons/                # Biểu tượng ứng dụng
    │   │   └── icon.icns
    │   └── src/                  # Mã nguồn Rust
    │       ├── lib.rs
    │       └── main.rs
    └── .github/                  # Cấu hình GitHub (workflows)
        └── workflows/
            └── build.yml         # Workflow CI/CD cho quá trình build

```

## 🚀 Cài Đặt & Thiết Lập

Để chạy dự án này cục bộ, hãy làm theo các bước sau:

### Điều Kiện Tiên Quyết

*   **Node.js & Pnpm:** Đảm bảo bạn đã cài đặt Node.js (phiên bản LTS) và Pnpm.
*   **Rust & Cargo:** Cài đặt Rust và Cargo thông qua `rustup`. Tauri yêu cầu môi trường Rust.
*   **Git:** Để clone repository.

### Các Bước

1.  **Clone repository:**
    ```bash
    git clone https://github.com/tin2709/UmlApp.git # Thay thế nếu repo của bạn khác

2.  **Cài đặt dependencies:**
    Dự án sử dụng PNPM. Đảm bảo bạn đã cài đặt PNPM toàn cục (`npm install -g pnpm`).
    ```bash
    pnpm install
    ```
    Thao tác này sẽ cài đặt cả các dependencies của frontend và các dependencies cần thiết cho Tauri (Rust).

3.  **Build ứng dụng (Tùy chọn, để tạo bản release):**
    ```bash
    pnpm tauri build
    ```
    Lệnh này sẽ tạo ra một gói cài đặt ứng dụng desktop cho hệ điều hành hiện tại của bạn trong thư mục `src-tauri/target/release/bundle/`.

### Chạy Ứng Dụng

1.  **Chạy ở chế độ phát triển:**
    ```bash
    pnpm tauri dev
    ```
    Lệnh này sẽ khởi động server Vite cho frontend và một phiên bản Tauri, tự động mở cửa sổ ứng dụng desktop và tải giao diện người dùng. Các thay đổi trong mã nguồn frontend sẽ được cập nhật nóng (hot-reloaded).

## 💡 Cách Sử Dụng

*   **Tạo Dự Án Mới:** Bắt đầu bằng cách tạo một dự án mới để sắp xếp các biểu đồ của bạn.
*   **Thêm Danh Mục:** Trong một dự án, bạn có thể tạo các danh mục để phân loại các biểu đồ.
*   **Mở Trình Chỉnh Sửa UML:** Chọn một danh mục hoặc biểu đồ để mở trình chỉnh sửa UML.
*   **Gõ Mã PlantUML:** Nhập mã PlantUML vào vùng soạn thảo. Biểu đồ sẽ tự động được hiển thị ở chế độ xem trước bên cạnh.
*   **Quản Lý Biểu Đồ:** Sử dụng các tính năng kéo và thả để sắp xếp lại danh mục và biểu đồ của bạn.
*   **Xem Trước & Xuất:** Xem trước biểu đồ của bạn và lưu hoặc xuất chúng khi hoàn thành.


---