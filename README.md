<!DOCTYPE html>
<html lang="vi">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Trang Liên Kết Của Bạn</title>
    <!-- Tải Tailwind CSS để tạo kiểu nhanh chóng và đẹp mắt -->
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        /* Thiết lập font Inter cho trải nghiệm đọc tốt nhất */
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@100..900&display=swap');
        body {
            font-family: 'Inter', sans-serif;
            background-color: #f3f4f6; /* Nền xám nhạt */
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: flex-start; /* Bắt đầu từ phía trên màn hình */
            padding-top: 2rem;
        }
        .container {
            width: 100%;
            max-width: 480px; /* Chiều rộng tối đa cho thiết bị di động/trung bình */
        }
        .link-card {
            transition: transform 0.2s, box-shadow 0.2s;
        }
        .link-card:hover {
            transform: translateY(-2px);
            box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05);
        }
    </style>
</head>
<body class="bg-gray-50">
    <div class="container p-4">
        <!-- Phần Đầu Trang -->
        <header class="text-center mb-10">
            <!-- Ảnh đại diện/Placeholder -->
            <div class="w-24 h-24 mx-auto mb-4 bg-gray-300 rounded-full flex items-center justify-center overflow-hidden border-4 border-white shadow-lg">
                <!-- Bạn có thể thay thế placeholder này bằng ảnh đại diện thật của mình -->
                <svg xmlns="https://drive.google.com/file/d/1D-Q8oF8-m5bWi-Bttdx5uK9mnwnG3ftu/view?usp=sharing" class="w-12 h-12 text-gray-600" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M16 7a4 4 0 11-8 0 4 4 0 018 0zM12 14a7 7 0 00-7 7h14a7 7 0 00-7-7z" />
                </svg>
            </div>
            <h1 id="user-name" class="text-3xl font-extrabold text-gray-800 mb-1">Tên Của Bạn</h1>
            <p id="user-bio" class="text-gray-500 font-medium">@Tóm Tắt Ngắn Về Bạn (VD: Người sáng tạo | Kỹ sư)</p>
        </header>

        <!-- Danh Sách Các Liên Kết -->
        <!-- Đã loại bỏ space-y-4 khỏi main vì các nhóm đã tự quản lý khoảng cách -->
        <main id="links-container">
            <!-- Liên kết sẽ được thêm vào đây bằng JavaScript -->
        </main>

        <!-- Phần Chân Trang -->
        <footer class="mt-12 text-center text-gray-400 text-sm">
            <p>Được tạo miễn phí bằng HTML, CSS & JavaScript</p>
        </footer>
    </div>

    <script>
        // 1. Cấu hình thông tin cá nhân của bạn
        const userName = "RBT BIDV SÔNG HÀN"; // Thay thế bằng tên của bạn
        const userBio = "BIDV | RBT | SÔNG HÀN"; // Thay thế bằng tiểu sử ngắn

        // 2. Danh sách các liên kết của bạn (THAY ĐỔI DỮ LIỆU Ở ĐÂY)
        // Dữ liệu được tổ chức thành Mảng các Nhóm (Group), mỗi nhóm có groupTitle và mảng links riêng.
        const linksData = [
            {
                groupTitle: "XỬ LÝ CHUNG",
                links: [
                    {
                        title: "Phối hợp xử lý hồ sơ tín dụng",
                        url: "https://docs.google.com/spreadsheets/d/1yt5INmDWv6QaxDXdxNNwScqSrfznrqW5FhuMkveby54/edit?usp=sharing",
                        iconClass: "youtube"
                    },
                ]
            },
            {
                groupTitle: "QUÁN TRỊ TÍN DỤNG",
                links: [
                    {
                        title: "NHẬT KÝ CÔNG VIỆC CỦA CÁN BỘ HỖ TRỢ VAY LS",
                        url: "https://docs.google.com/spreadsheets/d/1MErJLhm9TelPZmF40W0v4quretFALgFKBD96Pr72whE/edit?usp=sharing

",
                        iconClass: "globe"
                    },
                    {
                        title: "ĐÁNH GIÁ HIỆU QUẢ CỦA CÁN BỘ HỖ TRỢ VAY LS",
                        url: "https://docs.google.com/spreadsheets/d/1TmIgee84N-o5TJCKe9SNj9LlRFNH_L67Vh7UnKRWFPY/edit?usp=sharing",
                        iconClass: "linkedin"
                    },
                ]
            },
            {
                groupTitle: "Tài Liệu Khác",
                links: [
                    {
                        title: "Tài Liệu Hướng Dẫn (PDF)",
                        url: "https://drive.google.com/yourdocument",
                        iconClass: "file-text"
                    },
                ]
            },
        ];

        // 3. Hàm tạo biểu tượng (Icon) dựa trên tên
        // Sử dụng Lucide Icons (Inline SVG)
        function getIconSVG(iconName) {
            let path;
            switch (iconName) {
                case 'youtube':
                    path = '<path d="M15 13.8V5.2L20 9.5L15 13.8Z"/><path d="M21.5 10.4C21.5 11.4 21.5 12.6 21.5 13.6C21.5 16.5 21.3 19 20.9 20C20.4 21.2 19.3 21.7 17.8 21.8C16.2 21.9 13 22 12 22C11 22 7.8 21.9 6.2 21.8C4.7 21.7 3.6 21.2 3.1 20.0C2.7 19 2.5 16.5 2.5 13.6C2.5 12.6 2.5 11.4 2.5 10.4C2.5 7.5 2.7 5 3.1 4C3.6 2.8 4.7 2.3 6.2 2.2C7.8 2.1 11 2 12 2C13 2 16.2 2.1 17.8 2.2C19.3 2.3 20.4 2.8 20.9 4.0C21.3 5 21.5 7.5 21.5 10.4Z"/>';
                    break;
                case 'facebook':
                    path = '<path d="M18 2h-3a5 5 0 0 0-5 5v3H7v4h3v8h4v-8h3l1-4h-4V7a1 1 0 0 1 1-1h3z"/>';
                    break;
                case 'linkedin':
                    path = '<path d="M16 8a6 6 0 0 1 6 6v7h-4v-7a2 2 0 0 0-2-2 2 2 0 0 0-2 2v7h-4v-7a6 6 0 0 1 6-6z"/><rect width="4" height="12" x="2" y="9"/><circle cx="4" cy="4" r="2"/>';
                    break;
                case 'file-text':
                    path = '<path d="M15 2H6a2 2 0 0 0-2 2v16a2 2 0 0 0 2 2h12a2 2 0 0 0 2-2V7z"/><path d="M14 2v4a2 2 0 0 0 2 2h4"/><line x1="16" x2="8" y1="13" y2="13"/><line x1="16" x2="8" y1="17" y2="17"/><line x1="10" x2="8" y1="9" y2="9"/>';
                    break;
                case 'globe':
                default:
                    path = '<circle cx="12" cy="12" r="10"/><path d="M12 2a14.5 14.5 0 0 0 0 20 14.5 14.5 0 0 0 0-20"/><path d="M2 12h20"/>';
            }

            return `<svg xmlns="http://www.w3.org/2000/svg" class="w-6 h-6 mr-3 flex-shrink-0 text-white group-hover:text-gray-200" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">${path}</svg>`;
        }


        // 4. Hàm render (hiển thị) các liên kết
        function renderLinks() {
            // Cập nhật thông tin người dùng
            document.getElementById('user-name').textContent = userName;
            document.getElementById('user-bio').textContent = userBio;

            const container = document.getElementById('links-container');
            container.innerHTML = ''; // Xóa nội dung cũ

            // Lặp qua từng nhóm liên kết
            linksData.forEach(group => {
                // 1. Tạo tiêu đề nhóm (h2)
                const groupTitleElement = document.createElement('h2');
                groupTitleElement.textContent = group.groupTitle;
                // Sử dụng Tailwind để tạo kiểu cho tiêu đề nhóm và thêm khoảng cách
                groupTitleElement.className = 'text-lg font-bold text-gray-700 mt-6 mb-3 pt-3 border-t border-gray-300 first:mt-0 first:pt-0 first:border-t-0';
                
                container.appendChild(groupTitleElement);

                // 2. Tạo một div chứa các liên kết của nhóm, với khoảng cách giữa các liên kết
                const groupLinksContainer = document.createElement('div');
                groupLinksContainer.className = 'space-y-4 mb-8'; // Khoảng cách giữa các thẻ liên kết

                // 3. Lặp qua các liên kết trong nhóm
                group.links.forEach(link => {
                    const iconSVG = getIconSVG(link.iconClass);

                    const linkElement = document.createElement('a');
                    linkElement.href = link.url;
                    linkElement.target = "_blank"; // Mở liên kết trong tab mới
                    // Màu sắc vẫn là xanh dương, nhưng bạn có thể thay đổi bằng cách sửa bg-blue-600
                    linkElement.className = 'link-card block w-full bg-blue-600 hover:bg-blue-700 text-white font-bold py-4 px-6 rounded-xl shadow-md flex items-center justify-center transition duration-300 ease-in-out group';
                    
                    linkElement.innerHTML = `
                        ${iconSVG}
                        <span class="truncate">${link.title}</span>
                    `;

                    groupLinksContainer.appendChild(linkElement);
                });

                container.appendChild(groupLinksContainer);
            });
        }

        // Chạy hàm render khi trang tải xong
        document.addEventListener('DOMContentLoaded', renderLinks);
    </script>
</body>
</html>
