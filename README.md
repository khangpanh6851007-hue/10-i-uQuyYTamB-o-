# 🪷 Phật Pháp Tôn Nghiêm - Giao Diện 5.0 

Hệ thống website tĩnh tích hợp giáo lý Phật giáo cốt lõi, tích hợp tính năng **Giọng đọc Chị Google (Web Speech API)** và **Hệ thống tính điểm luật nhân quả (Phạm luật phạt gấp đôi)**. Được tối ưu hóa chuyên biệt để chạy trực tiếp trên các môi trường lập trình di động như **Acode** hoặc **TrebEdit** trên Android.

---

## 📱 Tính Năng Nổi Bật (Phiên bản 5.0)

1. **Giao Diện Kính Mờ (Glassmorphism):** Thiết kế hiện đại, sang trọng với tông màu tối kết hợp ánh sáng vàng kim (`#d9a74a`), mang lại cảm giác tĩnh tại, trang nghiêm.
2. **10 Điều Quy Y Tam Bảo:** Trình bày rõ ràng từng điều nương tựa Phật - Pháp - Tăng kèm theo nút phát âm thanh.
3. **10 Điều Ngăn Cấm & Giới Luật:** Danh sách các giới luật căn bản giúp người tu học giữ tâm trong sạch.
4. **Giọng Đọc "Chị Google" (Web Speech API):** Tích hợp sẵn bộ tổng hợp giọng nói tiếng Việt tự động đọc văn bản, tiêu đề hoặc nội dung giáo lý khi người dùng tương tác.
5. **Hệ Thống Phạt Gấp Đôi Nhân Quả:** Tính năng mô phỏng tính điểm nghiệp báo. Nếu người dùng chọn ô **"Cố ý phạm luật"**, hệ thống sẽ tự động nhân đôi hình phạt và đưa ra lời khuyên sám hối.
6. **Tối Ưu Mobile IDE (Acode / TrebEdit):** Toàn bộ mã nguồn được gom gọn trong một file `index.html` duy nhất (Single File Component), sử dụng CDN cho Tailwind CSS và FontAwesome giúp chạy mượt mà ngay trên điện thoại mà không cần cài đặt NodeJS hay Terminal phức tạp.

---

## 🛠️ Hướng Dẫn Cài Đặt Trên Acode / TrebEdit

Để chạy dự án này trên điện thoại Android thông qua ứng dụng **Acode** hoặc **TrebEdit**, bạn thực hiện theo các bước sau:

1. **Tạo file mới:**
   * Mở ứng dụng **Acode** hoặc **TrebEdit**.
   * Tạo một file mới và đặt tên là `index.html`.
2. **Dán mã nguồn:**
   * Sao chép toàn bộ mã HTML ở phần code bên dưới và dán vào file `index.html` vừa tạo.
3. **Chạy thử nghiệm (Preview):**
   * Trên **Acode**: Nhấn vào biểu tượng **Play** (hoặc nút xem trước trình duyệt) ở góc trên bên phải.
   * Trên **TrebEdit**: Nhấn nút **Run** để xem giao diện trực tiếp trên trình duyệt tích hợp.

---

## 📄 Mã Nguồn Đầy Đủ (`index.html`)

```html
<!DOCTYPE html>
<html lang="vi" class="dark">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Phật Pháp Tôn Nghiêm - 10 Điều Quy Y & Giới Luật</title>
    <!-- Tailwind CSS 3.4+ -->
    <script src="[https://cdn.tailwindcss.com](https://cdn.tailwindcss.com)"></script>
    <script>
        tailwind.config = {
            darkMode: 'class',
            theme: {
                extend: {
                    colors: {
                        gold: {
                            50: '#fdf8ec',
                            100: '#fbeed5',
                            500: '#d9a74a',
                            600: '#b8862b',
                            700: '#946722',
                        },
                        zen: {
                            900: '#0f172a',
                            800: '#1e293b',
                            700: '#334155',
                        }
                    }
                }
            }
        }
    </script>
    <!-- FontAwesome & Google Fonts -->
    <link rel="stylesheet" href="[https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css](https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css)">
    <link href="[https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@300;400;500;600;700&family=Playfair+Display:wght@600;700&display=swap](https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@300;400;500;600;700&family=Playfair+Display:wght@600;700&display=swap)" rel="stylesheet">
    <style>
        body { font-family: 'Plus Jakarta Sans', sans-serif; }
        .font-heading { font-family: 'Playfair Display', serif; }
        .glass-panel {
            background: rgba(30, 41, 59, 0.7);
            backdrop-filter: blur(16px);
            -webkit-backdrop-filter: blur(16px);
            border: 1px solid rgba(217, 167, 74, 0.2);
        }
        .glow-gold {
            box-shadow: 0 0 25px rgba(217, 167, 74, 0.15);
        }
        ::-webkit-scrollbar { width: 8px; }
        ::-webkit-scrollbar-track { background: #0f172a; }
        ::-webkit-scrollbar-thumb { background: #b8862b; border-radius: 4px; }
    </style>
</head>
<body class="bg-zen-900 text-slate-100 min-h-screen selection:bg-gold-500 selection:text-zen-900 relative overflow-x-hidden">

    <div class="absolute top-0 left-1/2 -translate-x-1/2 w-[600px] h-[600px] bg-gold-600/10 rounded-full blur-[140px] pointer-events-none"></div>

    <header class="sticky top-0 z-50 glass-panel border-b border-gold-500/20">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 h-20 flex items-center justify-between">
            <div class="flex items-center space-x-3">
                <div class="w-12 h-12 rounded-xl bg-gradient-to-tr from-gold-600 to-gold-400 flex items-center justify-center glow-gold text-zen-900 text-2xl font-bold">
                    <i class="fa-solid fa-dharmachakra"></i>
                </div>
                <div>
                    <h1 class="font-heading text-xl font-bold text-gold-400">Phật Pháp Tôn Nghiêm</h1>
                    <p class="text-xs text-slate-400">Giao diện 5.0 • Tích hợp Acode / TrebEdit</p>
                </div>
            </div>

            <div class="flex items-center space-x-3">
                <button onclick="toggleVoiceReader()" id="voiceBtn" class="px-4 py-2 rounded-xl bg-gold-600/20 hover:bg-gold-600/30 text-gold-400 border border-gold-500/30 transition-all flex items-center space-x-2 text-sm font-medium">
                    <i class="fa-solid fa-volume-high"></i>
                    <span class="hidden sm:inline">Giọng Chị Google</span>
                </button>
            </div>
        </div>
    </header>

    <main class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-10 space-y-16">
        <section class="text-center space-y-4 max-w-3xl mx-auto">
            <span class="px-4 py-1.5 rounded-full text-xs font-semibold bg-gold-500/10 text-gold-400 border border-gold-500/20 inline-block">
                NAM MÔ BỔN SƯ THÍCH CA MÂU NI PHẬT
            </span>
            <h2 class="font-heading text-4xl sm:text-5xl font-bold text-transparent bg-clip-text bg-gradient-to-r from-gold-300 via-gold-500 to-gold-600">
                Tam Bảo Gia Trì & Giới Luật Minh Tâm
            </h2>
            <p class="text-slate-300 text-base sm:text-lg">
                Hệ thống giáo lý cốt lõi dành cho người tu học. Ghi nhớ quy y, giữ gìn giới luật, thấu triệt luật nhân quả "phạm luật phạt gấp đôi".
            </p>
        </section>

        <!-- 10 ĐIỀU QUY Y -->
        <section class="space-y-6">
            <div class="flex items-center space-x-4 border-b border-gold-500/20 pb-4">
                <div class="w-10 h-10 rounded-lg bg-gold-500/10 flex items-center justify-center text-gold-400 text-xl">
                    <i class="fa-solid fa-gem"></i>
                </div>
                <div>
                    <h3 class="font-heading text-2xl font-bold text-gold-400">10 Điều Quy Y Tam Bảo</h3>
                    <p class="text-sm text-slate-400">Nương tựa Phật - Pháp - Tăng để soi sáng con đường tâm thức</p>
                </div>
            </div>
            <div class="grid grid-cols-1 md:grid-cols-2 gap-6" id="tamBaoContainer"></div>
        </section>

        <!-- 10 ĐIỀU NGĂN CẤM -->
        <section class="space-y-6">
            <div class="flex items-center space-x-4 border-b border-gold-500/20 pb-4">
                <div class="w-10 h-10 rounded-lg bg-red-500/10 flex items-center justify-center text-red-400 text-xl">
                    <i class="fa-solid fa-shield-halved"></i>
                </div>
                <div>
                    <h3 class="font-heading text-2xl font-bold text-red-400">10 Điều Ngăn Cấm & Luật Phạt Gấp Đôi</h3>
                    <p class="text-sm text-slate-400">Giới luật nghiêm minh - Cố ý phạm luật quả báo nhân đôi</p>
                </div>
            </div>
            <div class="grid grid-cols-1 md:grid-cols-2 gap-6" id="gioiLuatContainer"></div>
        </section>

        <!-- TÍNH NĂNG MỚI: PHẠT GẤP ĐÔI -->
        <section class="glass-panel rounded-3xl p-6 sm:p-8 glow-gold space-y-6">
            <div class="text-center space-y-2">
                <h3 class="font-heading text-2xl font-bold text-gold-400"><i class="fa-solid fa-calculator mr-2"></i>Hệ Thống Phạt Gấp Đôi Nhân Quả</h3>
                <p class="text-slate-400 text-sm">Chọn điều luật bạn đã vi phạm để tính toán mức độ nghiệp lực.</p>
            </div>
            <div class="max-w-xl mx-auto space-y-4">
                <div>
                    <label class="block text-sm font-medium text-slate-300 mb-2">Chọn lỗi vi phạm:</label>
                    <select id="violationSelect" class="w-full bg-zen-800 border border-gold-500/30 rounded-xl px-4 py-3 text-slate-100 focus:outline-none focus:border-gold-500">
                        <option value="1">1. Sát sinh (Cố ý hại mạng sống)</option>
                        <option value="2">2. Trộm cắp (Lấy của không cho)</option>
                        <option value="3">3. Tà dâm (Sai phạm hạnh)</option>
                        <option value="4">4. Nói dối (Lời sai sự thật)</option>
                        <option value="5">5. Uống rượu/Chất kích thích (Mê mờ trí tuệ)</option>
                    </select>
                </div>
                <div class="flex items-center space-x-4">
                    <label class="flex items-center space-x-2 cursor-pointer">
                        <input type="checkbox" id="isIntentional" class="w-5 h-5 rounded border-gold-500 text-gold-600 focus:ring-gold-500 bg-zen-800">
                        <span class="text-sm font-medium text-amber-300">Cố ý phạm luật (Nhân đôi hình phạt)</span>
                    </label>
                </div>
                <button onclick="calculatePenalty()" class="w-full py-3 rounded-xl bg-gradient-to-r from-gold-600 to-gold-500 text-zen-900 font-bold hover:opacity-90 transition-all shadow-lg">
                    Xác Định Nghiệp Báo & Đọc Kết Quả
                </button>
                <div id="penaltyResult" class="hidden p-4 rounded-xl bg-red-950/40 border border-red-500/30 text-red-200 text-sm space-y-2"></div>
            </div>
        </section>
    </main>

    <footer class="border-t border-gold-500/20 py-8 mt-20 text-center text-sm text-slate-400 space-y-2">
        <p>Phát triển tối ưu cho môi trường <strong class="text-gold-400">Acode</strong> và <strong class="text-gold-400">TrebEdit</strong> trên Android.</p>
        <p>Nam Mô A Di Đà Phật • Nguyện đem công đức này hướng về khắp tất cả.</p>
    </footer>

    <script>
        const tamBaoData = [
            { id: 1, title: "Quy y Phật - Đấng Giác Ngộ", desc: "Nguyện trọn đời nương tựa Phật, bậc Đạo Sư thiên nhân, không nương tựa thần linh tà giáo khác." },
            { id: 2, title: "Quy y Pháp - Chơn lý từ bi", desc: "Nguyện trọn đời nương tựa Chánh Pháp, con đường chuyển hóa khổ đau, đạt đến giác ngộ." },
            { id: 3, title: "Quy y Tăng - Đoàn thể thanh tịnh", desc: "Nguyện trọn đời nương tựa Tăng đoàn, những bậc tu hành chân chính thực hành giới luật." },
            { id: 4, title: "Giữ vững tâm tư Bồ Đề", desc: "Luôn hướng tâm về sự thiện lương, cứu khổ ban vui cho muôn loài." },
            { id: 5, title: "Tôn kính hình tượng Tam Bảo", desc: "Kính trọng tôn tượng Phật, kinh điển pháp bảo và các bậc chư Tăng." },
            { id: 6, title: "Thực hành sám hối nghiệp chướng", desc: "Mỗi ngày tự xét lỗi mình, sám hối các nghiệp bất thiện đã tạo." },
            { id: 7, title: "Phát nguyện bố thí, chia sẻ", desc: "Dùng tài sản và công sức để giúp đỡ những mảnh đời khó khăn, bất hạnh." },
            { id: 8, title: "Hộ trì Tam Bảo hưng long", desc: "Góp phần gìn giữ, bảo vệ và phát triển các giá trị chánh pháp ở thế gian." },
            { id: 9, title: "Tinh tấn thiền định, niệm Phật", desc: "Duy trì sự tĩnh lặng trong tâm hồn qua việc thực hành thiền và niệm danh hiệu Phật." },
            { id: 10, title: "Hồi hướng công đức vô lượng", desc: "Đem mọi phước báu tu tập được chia sẻ cho tất cả chúng sinh đồng thành Phật đạo." }
        ];

        const gioiLuatData = [
            { id: 1, title: "Không sát sinh", desc: "Tuyệt đối không hại mạng người và súc vật, bảo vệ sự sống muôn loài." },
            { id: 2, title: "Không trộm cắp", desc: "Không lấy những gì người khác không cho, không tham lam của bất nghĩa." },
            { id: 3, title: "Không tà dâm", desc: "Giữ gìn sự trong sạch trong quan hệ gia đình, không vi phạm luân thường đạo lý." },
            { id: 4, title: "Không nói dối", desc: "Nói lời chân thật, không thêu dệt, không nói lưỡi hai chiều, không lời ác độc." },
            { id: 5, title: "Không uống rượu & chất kích thích", desc: "Giữ tâm trí minh mẫn, không để chất làm mờ trí tuệ chi phối." },
            { id: 6, title: "Không trang sức, xức dầu thơm lòe loẹt", desc: "Giữ lối sống giản dị, không chạy theo hình thức sục sôi dục vọng." },
            { id: 7, title: "Không xem hát xướng, ca múa quá độ", desc: "Tránh xa những cám dỗ âm thanh, sắc tướng làm tâm trí dao động." },
            { id: 8, title: "Không nằm ngồi giường cao rộng, sang trọng", desc: "Thực hành đời sống khiêm tốn, biết đủ." },
            { id: 9, title: "Không ăn phi thời (ăn quá ngọ)", desc: "Kiểm soát dục vọng ăn uống, giữ tâm hồn nhẹ nhàng." },
            { id: 10, title: "Không giữ tiền bạc, vàng ngọc", desc: "Xả bỏ tâm chấp trước vào vật chất thế gian." }
        ];

        function renderContent() {
            document.getElementById('tamBaoContainer').innerHTML = tamBaoData.map(item => `
                <div class="glass-panel p-6 rounded-2xl hover:border-gold-500/50 transition-all space-y-3">
                    <div class="flex items-center justify-between">
                        <span class="text-xs font-bold text-gold-400 bg-gold-500/10 px-3 py-1 rounded-full">Điều ${item.id}</span>
                        <button onclick="speakText('${item.title}. ${item.desc}')" class="text-gold-400 hover:text-gold-300 text-sm">
                            <i class="fa-solid fa-volume-high"></i>
                        </button>
                    </div>
                    <h4 class="font-heading text-lg font-bold text-slate-100">${item.title}</h4>
                    <p class="text-sm text-slate-300">${item.desc}</p>
                </div>
            `).join('');

            document.getElementById('gioiLuatContainer').innerHTML = gioiLuatData.map(item => `
                <div class="glass-panel p-6 rounded-2xl hover:border-red-500/50 transition-all space-y-3">
                    <div class="flex items-center justify-between">
                        <span class="text-xs font-bold text-red-400 bg-red-500/10 px-3 py-1 rounded-full">Điều Cấm ${item.id}</span>
                        <button onclick="speakText('${item.title}. ${item.desc}')" class="text-red-400 hover:text-red-300 text-sm">
                            <i class="fa-solid fa-volume-high"></i>
                        </button>
                    </div>
                    <h4 class="font-heading text-lg font-bold text-slate-100">${item.title}</h4>
                    <p class="text-sm text-slate-300">${item.desc}</p>
                </div>
            `).join('');
        }

        function speakText(text) {
            if ('speechSynthesis' in window) {
                window.speechSynthesis.cancel();
                const utterance = new SpeechSynthesisUtterance(text);
                utterance.lang = 'vi-VN';
                utterance.rate = 0.95;
                utterance.pitch = 1.1;
                window.speechSynthesis.speak(utterance);
            }
        }

        function toggleVoiceReader() {
            speakText("Chào mừng bạn đến với hệ thống Phật pháp tôn nghiêm trên Acode TrebEdit.");
        }

        function calculatePenalty() {
            const select = document.getElementById('violationSelect');
            const isIntentional = document.getElementById('isIntentional').checked;
            const resultDiv = document.getElementById('penaltyResult');

            let violationName = select.options[select.selectedIndex].text;
            let karmaScore = select.value * 10;

            if (isIntentional) {
                karmaScore *= 2;
                resultDiv.innerHTML = `
                    <p class="font-bold text-red-400"><i class="fa-solid fa-triangle-exclamation mr-2"></i>CẢNH BÁO: Cố ý phạm luật - HÌNH PHẠT NHÂN ĐÔI!</p>
                    <p>Lỗi: <strong>${violationName}</strong></p>
                    <p>Hệ số nghiệp báo: <strong>${karmaScore} điểm</strong>.</p>
                `;
                speakText("Cảnh báo! Cố ý phạm luật, hình phạt nhân đôi!");
            } else {
                resultDiv.innerHTML = `
                    <p class="font-bold text-amber-400"><i class="fa-solid fa-circle-info mr-2"></i>Kết quả:</p>
                    <p>Lỗi vô ý: <strong>${violationName}</strong></p>
                    <p>Hệ số nghiệp báo: <strong>${karmaScore} điểm</strong>.</p>
                `;
                speakText("Điểm nghiệp báo đã ghi nhận.");
            }
            resultDiv.classList.remove('hidden');
        }

        window.onload = renderContent;
    </script>
</body>
</html>
