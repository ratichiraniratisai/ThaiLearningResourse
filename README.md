<html lang="th">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>ระบบฐานข้อมูลแหล่งเรียนรู้และแหล่งท่องเที่ยวท้องถิ่น</title>

    <!-- Google Fonts: Sarabun -->
    <link rel="preconnect" href="https://fonts.googleapis.com" />
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
    <link
      href="https://fonts.googleapis.com/css2?family=Sarabun:wght@300;400;500;600;700&display=swap"
      rel="stylesheet"
    />

    <!-- Tailwind CSS -->
    <script src="https://cdn.tailwindcss.com"></script>
    <script>
      tailwind.config = {
        theme: {
          extend: {
            fontFamily: {
              sans: ["Sarabun", "sans-serif"],
            },
            colors: {
              "thai-primary": "#00695c",
              "thai-secondary": "#ffca28",
              "thai-accent": "#e0f2f1",
              "ministry-orange": "#f57c00",
            },
          },
        },
      };
    </script>
  </head>
  <body class="bg-gray-50 text-gray-800 font-sans">
    <div class="min-h-screen flex flex-col">
      <!-- Header -->
      <header class="bg-white shadow-sm border-b border-gray-200">
        <div
          class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-4 flex items-center justify-between"
        >
          <div class="flex items-center gap-3">
            <div
              class="w-10 h-10 rounded-xl bg-thai-primary/10 flex items-center justify-center"
            >
              <span class="text-thai-primary font-bold text-lg">LR</span>
            </div>
            <div>
              <h1
                class="text-lg sm:text-xl font-semibold text-thai-primary tracking-tight"
              >
                ระบบฐานข้อมูลแหล่งเรียนรู้และแหล่งท่องเที่ยวท้องถิ่น
              </h1>
              <p class="text-xs sm:text-sm text-gray-500">
                เชื่อมโยงแหล่งเรียนรู้-แหล่งท่องเที่ยวในชุมชนกับการจัดการเรียนรู้ของสถานศึกษา
              </p>
            </div>
          </div>
          <span
            class="hidden sm:inline-flex text-xs px-3 py-1 rounded-full bg-thai-accent text-thai-primary font-medium"
          >
            Prototype (HTML + JS เท่านั้น)
          </span>
        </div>
      </header>

      <!-- Main -->
      <main class="flex-1">
        <!-- Hero / Search -->
        <section
          class="bg-gradient-to-b from-thai-accent/80 to-transparent border-b border-gray-200"
        >
          <div
            class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-8 lg:py-10 grid lg:grid-cols-2 gap-8 items-center"
          >
            <!-- Hero text -->
            <div>
              <h2 class="text-2xl sm:text-3xl font-bold text-gray-900 mb-3">
                ค้นหาแหล่งเรียนรู้และแหล่งท่องเที่ยวท้องถิ่น
              </h2>
              <p class="text-sm sm:text-base text-gray-600 mb-4">
                เลือกจังหวัด และกรอกชื่ออำเภอที่ต้องการ ระบบจะสร้างตัวอย่าง
                <span class="font-semibold text-thai-primary">
                  วัด น้ำตก ทะเล หาด ทะเลสาบ อ่าว อ่างเก็บน้ำ ภูเขา ดอย
                  อุทยาน ป่า ตลาด ถนนคนเดิน พิพิธภัณฑ์
                </span>
                ครบทุกประเภทในทุกจังหวัด เพื่อใช้ประกอบการออกแบบหน่วยการเรียนรู้ฐานชุมชน
              </p>
              <ul class="text-xs sm:text-sm text-gray-600 space-y-1 mb-6">
                <li>• เลือกจังหวัด แล้วกรอกชื่ออำเภอ (หรือเว้นว่างก็ได้)</li>
                <li>• ระบบสร้างชื่อแหล่งท่องเที่ยว + คำอธิบาย + กลุ่มสาระ + ตัวชี้วัด</li>
                <li>• ใช้เป็นต้นแบบ / ไอเดีย แล้วเติมข้อมูลจริงของจังหวัดได้ภายหลัง</li>
              </ul>

              <!-- Search form -->
              <form
                id="searchForm"
                class="bg-white shadow-md rounded-2xl p-4 sm:p-5 border border-gray-100"
              >
                <div class="grid md:grid-cols-2 gap-4 mb-4">
                  <div>
                    <label
                      for="province"
                      class="block text-xs font-medium text-gray-700 mb-1"
                    >
                      จังหวัด <span class="text-red-500">*</span>
                    </label>
                    <select
                      id="province"
                      class="block w-full rounded-xl border-gray-300 text-sm focus:ring-thai-primary focus:border-thai-primary"
                      required
                    >
                      <option value="">-- เลือกจังหวัด --</option>
                    </select>
                  </div>
                  <div>
                    <label
                      for="district"
                      class="block text-xs font-medium text-gray-700 mb-1"
                    >
                      อำเภอ (พิมพ์เองได้)
                    </label>
                    <input
                      id="district"
                      type="text"
                      placeholder="เช่น เมืองเชียงใหม่, บางแค"
                      class="block w-full rounded-xl border-gray-300 text-sm focus:ring-thai-primary focus:border-thai-primary"
                    />
                  </div>
                </div>

                <div class="flex items-center justify-between gap-3">
                  <button
                    type="submit"
                    class="inline-flex items-center justify-center px-4 py-2.5 rounded-xl text-sm font-semibold text-white bg-thai-primary hover:bg-thai-primary/90 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-thai-primary"
                  >
                    ค้นหาแหล่งเรียนรู้ / แหล่งท่องเที่ยว
                  </button>
                  <p class="text-[11px] text-gray-500 text-right">
                    ถ้าไม่กรอกอำเภอ ระบบจะสร้างแหล่งท่องเที่ยวตัวอย่างทุกประเภทของจังหวัดนั้นให้
                  </p>
                </div>
              </form>
            </div>

            <!-- Hero panel -->
            <div
              class="hidden lg:block relative bg-white border border-thai-accent/60 rounded-3xl shadow-sm overflow-hidden"
            >
              <div class="absolute inset-0 bg-gradient-to-br from-thai-accent/60 via-white to-thai-secondary/40 opacity-70"></div>
              <div class="relative p-6 h-full flex flex-col justify-between">
                <div>
                  <h3
                    class="text-base font-semibold text-thai-primary mb-2 flex items-center gap-2"
                  >
                    แผงสรุปแหล่งเรียนรู้ท้องถิ่น
                    <span
                      class="inline-flex items-center px-2 py-0.5 rounded-full text-[10px] font-medium bg-white/80 text-thai-primary border border-thai-primary/20"
                    >
                      สำหรับครู / ศึกษานิเทศก์
                    </span>
                  </h3>
                  <div class="space-y-2 text-xs text-gray-700">
                    <p>• ใช้เป็นฐานข้อมูลต้นแบบในการออกแบบแผนการจัดการเรียนรู้</p>
                    <p>• เชื่อมโยงกับ PBL / ทัศนศึกษา / โครงงานฐานชุมชน</p>
                    <p>• สามารถดัดแปลงชื่อสถานที่ให้ตรงกับแหล่งท่องเที่ยวจริงในพื้นที่ได้</p>
                  </div>
                </div>

                <div class="mt-4 grid grid-cols-2 gap-2 text-[11px]">
                  <div class="bg-white/70 border border-white rounded-2xl p-3">
                    <p class="font-semibold text-gray-800 mb-1">
                      ตัวอย่างการใช้ในแผน
                    </p>
                    <ul class="list-disc list-inside space-y-1 text-gray-600">
                      <li>ศึกษาเรื่องระบบนิเวศน้ำตก / ทะเล / ป่า</li>
                      <li>สำรวจเศรษฐกิจชุมชนจากตลาด / ถนนคนเดิน</li>
                      <li>เรียนรู้ประวัติศาสตร์จากวัด / พิพิธภัณฑ์</li>
                    </ul>
                  </div>
                  <div class="bg-white/80 border border-white rounded-2xl p-3">
                    <p class="font-semibold text-gray-800 mb-1">
                      เชื่อมโยงมาตรฐาน
                    </p>
                    <p class="text-gray-600 mb-1">
                      เช่น ส 1.1, ส 2.1, ส 4.3, ว 8.1, ง 1.1, ค 4.1 ฯลฯ
                    </p>
                    <p class="text-gray-500">
                      ครูสามารถปรับให้ตรงหลักสูตรสถานศึกษาได้ทันที
                    </p>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </section>

        <!-- Results section -->
        <section class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-8">
          <div id="resultsContainer" class="min-h-[260px]">
            <!-- Initial empty state -->
            <div
              id="initialState"
              class="border-2 border-dashed border-thai-accent rounded-2xl p-6 flex flex-col sm:flex-row items-start sm:items-center gap-4 bg-white"
            >
              <div
                class="w-12 h-12 rounded-full bg-thai-accent flex items-center justify-center flex-shrink-0"
              >
                <span class="text-thai-primary font-bold text-lg">i</span>
              </div>
              <div>
                <h3 class="font-semibold text-gray-900 mb-1 text-sm sm:text-base">
                  พร้อมให้บริการค้นหาแหล่งเรียนรู้และแหล่งท่องเที่ยวในพื้นที่ของคุณ
                </h3>
                <p class="text-xs sm:text-sm text-gray-600">
                  โปรดเลือกจังหวัด และกรอกชื่ออำเภอ (หรือเว้นว่างได้)
                  จากนั้นกดปุ่ม “ค้นหาแหล่งเรียนรู้ / แหล่งท่องเที่ยว”
                  ระบบจะสร้างตัวอย่างแหล่งท่องเที่ยวครบทุกประเภทในจังหวัดนั้นให้โดยอัตโนมัติ
                </p>
              </div>
            </div>

            <!-- Dynamic result list -->
            <div id="resultsList" class="hidden mt-4 space-y-4"></div>
          </div>
        </section>
      </main>

      <!-- Footer -->
      <footer class="border-t border-gray-200 bg-white">
        <div
          class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-4 flex flex-col sm:flex-row items-center justify-between gap-2"
        >
          <p class="text-[11px] text-gray-500">
            ระบบต้นแบบเพื่อสาธิตแนวคิดฐานข้อมูลแหล่งเรียนรู้และแหล่งท่องเที่ยวท้องถิ่น
          </p>
          <p class="text-[11px] text-gray-400">
            พัฒนาในรูปแบบ HTML/JavaScript ไม่ใช้ React หรือ Vite
          </p>
        </div>
      </footer>
    </div>

    <!-- Plain JavaScript logic -->
    <script>
      // --------- ข้อมูลจังหวัดครบ 77 จังหวัด ----------
      const PROVINCES = [
        "กรุงเทพมหานคร",
        "กระบี่",
        "กาญจนบุรี",
        "กาฬสินธุ์",
        "กำแพงเพชร",
        "ขอนแก่น",
        "จันทบุรี",
        "ฉะเชิงเทรา",
        "ชลบุรี",
        "ชัยนาท",
        "ชัยภูมิ",
        "ชุมพร",
        "เชียงราย",
        "เชียงใหม่",
        "ตรัง",
        "ตราด",
        "ตาก",
        "นครนายก",
        "นครปฐม",
        "นครพนม",
        "นครราชสีมา",
        "นครศรีธรรมราช",
        "นครสวรรค์",
        "นนทบุรี",
        "นราธิวาส",
        "น่าน",
        "บึงกาฬ",
        "บุรีรัมย์",
        "ปทุมธานี",
        "ประจวบคีรีขันธ์",
        "ปราจีนบุรี",
        "ปัตตานี",
        "พระนครศรีอยุธยา",
        "พังงา",
        "พัทลุง",
        "พิจิตร",
        "พิษณุโลก",
        "เพชรบุรี",
        "เพชรบูรณ์",
        "แพร่",
        "พะเยา",
        "ภูเก็ต",
        "มหาสารคาม",
        "มุกดาหาร",
        "แม่ฮ่องสอน",
        "ยโสธร",
        "ยะลา",
        "ร้อยเอ็ด",
        "ระนอง",
        "ระยอง",
        "ราชบุรี",
        "ลพบุรี",
        "ลำปาง",
        "ลำพูน",
        "เลย",
        "ศรีสะเกษ",
        "สกลนคร",
        "สงขลา",
        "สตูล",
        "สมุทรปราการ",
        "สมุทรสงคราม",
        "สมุทรสาคร",
        "สระแก้ว",
        "สระบุรี",
        "สิงห์บุรี",
        "สุโขทัย",
        "สุพรรณบุรี",
        "สุราษฎร์ธานี",
        "สุรินทร์",
        "หนองคาย",
        "หนองบัวลำภู",
        "อ่างทอง",
        "อุดรธานี",
        "อุตรดิตถ์",
        "อุทัยธานี",
        "อุบลราชธานี",
        "อำนาจเจริญ"
      ];

      // --------- ประเภทแหล่งท่องเที่ยวหลัก ----------
      const ATTRACTION_TYPES = [
        "วัด",
        "น้ำตก",
        "ทะเล",
        "หาด",
        "ทะเลสาบ",
        "อ่าว",
        "อ่างเก็บน้ำ",
        "ภูเขา",
        "ดอย",
        "อุทยาน",
        "ป่า",
        "ตลาด",
        "ถนนคนเดิน",
        "พิพิธภัณฑ์"
      ];

      // --------- ข้อมูลแหล่งเรียนรู้/ท่องเที่ยวตัวอย่างแบบเฉพาะเจาะจง (ใช้ชื่อจริง/คุ้นหู) ----------
      const BASE_ATTRACTIONS = [
        {
          id: "bkk-01",
          name: "วัดพระแก้วและพระบรมมหาราชวัง",
          province: "กรุงเทพมหานคร",
          district: "พระนคร",
          type: "วัด",
          description:
            "ศูนย์กลางศิลปวัฒนธรรมและประวัติศาสตร์ชาติไทย เหมาะสำหรับบูรณาการสังคมศึกษา ภาษาไทย และประวัติศาสตร์",
          subjects: [
            "สังคมศึกษา ศาสนา และวัฒนธรรม",
            "ภาษาไทย",
            "ประวัติศาสตร์"
          ],
          standards: ["ส 1.1", "ส 4.3", "ท 1.1"],
          tags: ["วัด", "ประวัติศาสตร์", "ศิลปกรรม"]
        },
        {
          id: "cm-01",
          name: "วัดพระธาตุดอยสุเทพราชวรวิหาร",
          province: "เชียงใหม่",
          district: "เมืองเชียงใหม่",
          type: "วัด",
          description:
            "ปูชนียสถานคู่เมืองเชียงใหม่ เหมาะสำหรับเรียนรู้ภูมิประเทศ ความเชื่อ และวัฒนธรรมล้านนา",
          subjects: ["ภูมิศาสตร์", "สังคมศึกษา", "ประวัติศาสตร์ท้องถิ่น"],
          standards: ["ส 5.1", "ส 2.1"],
          tags: ["วัด", "ภูมิประเทศ", "วัฒนธรรมล้านนา"]
        },
        {
          id: "cm-02",
          name: "ดอยสุเทพ",
          province: "เชียงใหม่",
          district: "เมืองเชียงใหม่",
          type: "ดอย",
          description:
            "ดอยที่ตั้งวัดพระธาตุดอยสุเทพ มองเห็นภาพรวมภูมิประเทศเมืองเชียงใหม่ เหมาะสำหรับศึกษาภูมิประเทศและการตั้งถิ่นฐาน",
          subjects: ["ภูมิศาสตร์", "วิทยาศาสตร์", "สังคมศึกษา"],
          standards: ["ส 5.1", "ว 8.1"],
          tags: ["ดอย", "ภูมิประเทศ", "จุดชมวิว"]
        },
        {
          id: "cm-03",
          name: "ดอยอินทนนท์",
          province: "เชียงใหม่",
          district: "จอมทอง",
          type: "ดอย",
          description:
            "ยอดเขาที่สูงที่สุดในประเทศไทย เป็นแหล่งเรียนรู้เรื่องระบบนิเวศป่าดิบเขา ความหลากหลายทางชีวภาพ และภูมิอากาศ",
          subjects: ["วิทยาศาสตร์", "ภูมิศาสตร์"],
          standards: ["ว 8.1", "ส 5.1"],
          tags: ["ดอย", "อุทยาน", "ป่า"]
        },
        {
          id: "cr-01",
          name: "ดอยตุงและพระตำหนักดอยตุง",
          province: "เชียงราย",
          district: "แม่ฟ้าหลวง",
          type: "ดอย",
          description:
            "พื้นที่พัฒนาต้นแบบด้านเกษตรบนพื้นที่สูง การฟื้นฟูป่า และการพัฒนาคุณภาพชีวิตชุมชนบนดอย",
          subjects: ["สังคมศึกษา", "การงานอาชีพ", "วิทยาศาสตร์"],
          standards: ["ส 2.1", "ง 1.1", "ว 8.1"],
          tags: ["ดอย", "โครงการพัฒนา", "เกษตรบนพื้นที่สูง"]
        },
        {
          id: "pk-01",
          name: "พิพิธภัณฑ์ภูเก็ตไทยหัว",
          province: "ภูเก็ต",
          district: "เมืองภูเก็ต",
          type: "พิพิธภัณฑ์",
          description:
            "อาคารชิโนโปรตุกีสเก่าแก่ เล่าเรื่องราวประวัติศาสตร์ภูเก็ตและชุมชนชาวจีนโพ้นทะเล",
          subjects: ["ประวัติศาสตร์", "ศิลปะ", "สังคมศึกษา"],
          standards: ["ส 4.3"],
          tags: ["พิพิธภัณฑ์", "อาคารเก่า", "ชุมชนชาวจีน"]
        },
        {
          id: "pk-02",
          name: "หาดไม้ขาว",
          province: "ภูเก็ต",
          district: "ถลาง",
          type: "หาด",
          description:
            "ชายหาดเงียบสงบทางตอนเหนือของเกาะภูเก็ต เหมาะสำหรับศึกษาการท่องเที่ยวเชิงอนุรักษ์และระบบนิเวศชายฝั่ง",
          subjects: ["วิทยาศาสตร์", "สังคมศึกษา"],
          standards: ["ว 8.1", "ส 2.1"],
          tags: ["หาด", "ทะเล", "การท่องเที่ยวเชิงอนุรักษ์"]
        },
        {
          id: "cb-01",
          name: "พัทยาชายหาด",
          province: "ชลบุรี",
          district: "บางละมุง",
          type: "หาด",
          description:
            "ชายหาดสำคัญทางการท่องเที่ยวของภาคตะวันออก เหมาะสำหรับศึกษาผลกระทบของการท่องเที่ยวต่อเศรษฐกิจและสิ่งแวดล้อม",
          subjects: ["สังคมศึกษา", "วิทยาศาสตร์", "การงานอาชีพ"],
          standards: ["ส 2.1", "ว 8.1", "ง 1.1"],
          tags: ["หาด", "การท่องเที่ยว", "เศรษฐกิจชุมชน"]
        },
        {
          id: "kb-01",
          name: "อุทยานแห่งชาติน้ำตกห้วยแม่ขมิ้น",
          province: "กาญจนบุรี",
          district: "ศรีสวัสดิ์",
          type: "น้ำตก",
          description:
            "น้ำตกชั้นต่าง ๆ ท่ามกลางป่าอุดมสมบูรณ์ เหมาะเป็นห้องเรียนธรรมชาติเรื่องระบบนิเวศป่าไม้และแหล่งน้ำ",
          subjects: ["วิทยาศาสตร์", "ภูมิศาสตร์"],
          standards: ["ว 8.1"],
          tags: ["น้ำตก", "อุทยาน", "ป่า"]
        },
        {
          id: "kb-02",
          name: "เขาช้างเผือก",
          province: "กาญจนบุรี",
          district: "ทองผาภูมิ",
          type: "ภูเขา",
          description:
            "เส้นทางเดินป่าบนสันเขารูปสันคมมีด มองเห็นภูมิประเทศแบบภูเขาสลับซับซ้อน เหมาะสำหรับศึกษาภูมิประเทศและการท่องเที่ยวเชิงนิเวศ",
          subjects: ["ภูมิศาสตร์", "วิทยาศาสตร์"],
          standards: ["ส 5.1", "ว 8.1"],
          tags: ["ภูเขา", "เดินป่า", "ท่องเที่ยวเชิงนิเวศ"]
        },
        {
          id: "pkk-01",
          name: "อ่าวมะนาว",
          province: "ประจวบคีรีขันธ์",
          district: "เมืองประจวบคีรีขันธ์",
          type: "อ่าว",
          description:
            "อ่าวโค้งรูปพระจันทร์ แหล่งท่องเที่ยวสำคัญของจังหวัด เหมาะสำหรับศึกษาระบบนิเวศชายฝั่งและเศรษฐกิจชุมชนประมง",
          subjects: ["วิทยาศาสตร์", "สังคมศึกษา", "การงานอาชีพ"],
          standards: ["ว 8.1", "ส 2.1", "ง 1.1"],
          tags: ["อ่าว", "ทะเล", "ชุมชนประมง"]
        },
        {
          id: "rb-01",
          name: "เขางู (อุทยานหินเขางู)",
          province: "ราชบุรี",
          district: "เมืองราชบุรี",
          type: "ภูเขา",
          description:
            "ภูเขาหินปูนและแหล่งท่องเที่ยวใกล้เมือง ใช้เป็นแหล่งเรียนรู้เรื่องธรณีวิทยา การท่องเที่ยว และภูมิประเทศแบบหินปูน",
          subjects: ["วิทยาศาสตร์", "ภูมิศาสตร์", "สังคมศึกษา"],
          standards: ["ว 3.1", "ส 5.1"],
          tags: ["ภูเขา", "ธรณีวิทยา", "แหล่งท่องเที่ยวใกล้เมือง"]
        },
        {
          id: "kb-03",
          name: "หาดไร่เลย์",
          province: "กระบี่",
          district: "เมืองกระบี่",
          type: "หาด",
          description:
            "ชายหาดที่มีหน้าผาหินปูนล้อมรอบ เดินทางได้โดยทางเรือ เหมาะสำหรับศึกษาการท่องเที่ยวทางทะเลและระบบนิเวศชายฝั่ง",
          subjects: ["วิทยาศาสตร์", "สังคมศึกษา"],
          standards: ["ว 8.1", "ส 2.1"],
          tags: ["หาด", "ปีนผา", "ทะเล"]
        },
        {
          id: "kb-04",
          name: "อ่าวมาหยา (หมู่เกาะพีพี)",
          province: "กระบี่",
          district: "เมืองกระบี่",
          type: "อ่าว",
          description:
            "อ่าวที่มีชื่อเสียงระดับโลก น้ำทะเลใสและหาดทรายขาว เหมาะสำหรับศึกษาผลกระทบของการท่องเที่ยวต่อระบบนิเวศทางทะเล",
          subjects: ["วิทยาศาสตร์", "สังคมศึกษา"],
          standards: ["ว 8.1", "ส 2.1"],
          tags: ["อ่าว", "หมู่เกาะ", "การท่องเที่ยวทางทะเล"]
        },
        {
          id: "sn-01",
          name: "หมู่บ้านช้างบ้านตากลาง",
          province: "สุรินทร์",
          district: "ท่าตูม",
          type: "หมู่บ้านช้าง",
          description:
            "ชุมชนที่มีวัฒนธรรมการเลี้ยงช้างดั้งเดิม เหมาะสำหรับศึกษาวิถีชีวิตชุมชน ภูมิปัญญาท้องถิ่น และการท่องเที่ยวเชิงวัฒนธรรม",
          subjects: ["สังคมศึกษา", "การงานอาชีพ"],
          standards: ["ส 2.1", "ง 1.1"],
          tags: ["หมู่บ้านช้าง", "ภูมิปัญญาท้องถิ่น", "วัฒนธรรม"]
        },
        {
          id: "cm-04",
          name: "ป่าสนวัดจันทร์",
          province: "เชียงใหม่",
          district: "กัลยาณิวัฒนา",
          type: "ป่า",
          description:
            "พื้นที่ป่าสนและอ่างเก็บน้ำท่ามกลางขุนเขา เหมาะสำหรับศึกษาระบบนิเวศป่าเขตหนาวและการท่องเที่ยวเชิงธรรมชาติ",
          subjects: ["วิทยาศาสตร์", "สังคมศึกษา"],
          standards: ["ว 8.1"],
          tags: ["ป่าสน", "อ่างเก็บน้ำ", "ท่องเที่ยวเชิงธรรมชาติ"]
        }
      ];

      // --------- ฟังก์ชันช่วยสร้างข้อมูลแบบอัตโนมัติ (ทุกจังหวัด x ทุกประเภท) ----------
      function normalizeProvinceCoreName(province) {
        if (province === "กรุงเทพมหานคร") return "กรุงเทพ";
        return province.replace("จังหวัด", "").trim();
      }

      function defaultDistrictForProvince(province) {
        const core = normalizeProvinceCoreName(province);
        if (province === "กรุงเทพมหานคร") return "พระนคร";
        return `เมือง${core}`;
      }

      function createGenericAttraction(province, district, type, index) {
        const core = normalizeProvinceCoreName(province);
        let name = "";
        let description = "";
        let subjects = [];
        let standards = [];
        const tags = [type, "แหล่งท่องเที่ยว", "แหล่งเรียนรู้ชุมชน"];

        switch (type) {
          case "วัด":
            name = `วัดสำคัญประจำ${core}`;
            description = `วัดสำคัญของจังหวัด${province} ใช้จัดกิจกรรมทางศาสนา ประเพณี และเป็นศูนย์รวมจิตใจของชุมชนในอำเภอ${district}`;
            subjects = ["สังคมศึกษา ศาสนา และวัฒนธรรม", "ประวัติศาสตร์ท้องถิ่น"];
            standards = ["ส 1.1", "ส 1.2"];
            break;
          case "น้ำตก":
            name = `น้ำตก${core}`;
            description = `แหล่งน้ำตกและป่าไม้ในเขตภูเขาของจังหวัด${province} เหมาะสำหรับศึกษาระบบนิเวศ ป่าไม้ และการอนุรักษ์สิ่งแวดล้อม`;
            subjects = ["วิทยาศาสตร์", "ภูมิศาสตร์"];
            standards = ["ว 8.1"];
            break;
          case "ทะเล":
            name = `ชายฝั่งทะเล${core}`;
            description = `แนวชายฝั่งทะเลของจังหวัด${province} ใช้เป็นแหล่งเรียนรู้เรื่องระบบนิเวศชายฝั่ง การประมง และการท่องเที่ยวทางทะเล`;
            subjects = ["วิทยาศาสตร์", "สังคมศึกษา", "การงานอาชีพ"];
            standards = ["ว 8.1", "ส 2.1"];
            break;
          case "หาด":
            name = `หาด${core}`;
            description = `หาดทรายสำคัญในจังหวัด${province} เหมาะกับการเรียนรู้เรื่องการท่องเที่ยว เศรษฐกิจชุมชน และสิ่งแวดล้อมชายฝั่ง`;
            subjects = ["การงานอาชีพ", "สังคมศึกษา"];
            standards = ["ง 1.1", "ส 2.1"];
            break;
          case "ทะเลสาบ":
            name = `ทะเลสาบ${core}`;
            description = `แหล่งน้ำขนาดใหญ่ในจังหวัด${province} ใช้เป็นห้องเรียนธรรมชาติสำหรับศึกษาระบบนิเวศน้ำจืดและการใช้ประโยชน์จากทรัพยากรน้ำของชุมชน`;
            subjects = ["วิทยาศาสตร์", "สังคมศึกษา"];
            standards = ["ว 8.1"];
            break;
          case "อ่าว":
            name = `อ่าว${core}`;
            description = `พื้นที่อ่าวสำคัญของจังหวัด${province} เหมาะกับการศึกษาภูมิประเทศชายฝั่ง การประมง และการคมนาคมทางทะเล`;
            subjects = ["ภูมิศาสตร์", "วิทยาศาสตร์"];
            standards = ["ส 5.1"];
            break;
          case "อ่างเก็บน้ำ":
            name = `อ่างเก็บน้ำ${core}`;
            description = `แหล่งน้ำเพื่อการเกษตรและอุปโภคบริโภคในจังหวัด${province} สามารถใช้เรียนรู้การจัดการทรัพยากรน้ำและเศรษฐกิจชุมชน`;
            subjects = ["วิทยาศาสตร์", "การงานอาชีพ"];
            standards = ["ว 8.1", "ง 1.1"];
            break;
          case "ภูเขา":
            name = `ภูเขา${core}`;
            description = `ภูเขาสำคัญของจังหวัด${province} ใช้เรียนรู้ลักษณะภูมิประเทศ ภูมิอากาศ และความหลากหลายทางชีวภาพ`;
            subjects = ["ภูมิศาสตร์", "วิทยาศาสตร์"];
            standards = ["ส 5.1"];
            break;
          case "ดอย":
            name = `ดอย${core}`;
            description = `ดอยและพื้นที่สูงของจังหวัด${province} เหมาะสำหรับศึกษาวิถีชีวิตชุมชนบนพื้นที่สูง เกษตรกรรม และวัฒนธรรมเฉพาะถิ่น`;
            subjects = ["สังคมศึกษา", "การงานอาชีพ"];
            standards = ["ส 2.1", "ง 1.1"];
            break;
          case "อุทยาน":
            name = `อุทยานแห่งชาติ${core}`;
            description = `อุทยานแห่งชาติในจังหวัด${province} เป็นแหล่งเรียนรู้ด้านทรัพยากรธรรมชาติ การอนุรักษ์ และการท่องเที่ยวเชิงนิเวศ`;
            subjects = ["วิทยาศาสตร์", "สังคมศึกษา"];
            standards = ["ว 8.1", "ส 2.1"];
            break;
          case "ป่า":
            name = `ป่าอนุรักษ์${core}`;
            description = `พื้นที่ป่าอนุรักษ์ของจังหวัด${province} ใช้เป็นแหล่งเรียนรู้เรื่องความหลากหลายทางชีวภาพและการอนุรักษ์ป่าไม้`;
            subjects = ["วิทยาศาสตร์", "สังคมศึกษา"];
            standards = ["ว 8.1"];
            break;
          case "ตลาด":
            name = `ตลาดชุมชน${core}`;
            description = `ตลาดชุมชนในจังหวัด${province} สามารถใช้เป็นห้องเรียนจริงเรื่องการค้าขาย การคำนวณราคา และเศรษฐกิจฐานราก`;
            subjects = ["การงานอาชีพ", "คณิตศาสตร์", "สังคมศึกษา"];
            standards = ["ง 1.1", "ค 4.1"];
            break;
          case "ถนนคนเดิน":
            name = `ถนนคนเดิน${core}`;
            description = `ถนนคนเดินในจังหวัด${province} แหล่งรวมอาหาร ศิลปะ และงานหัตถกรรม สะท้อนอัตลักษณ์ของชุมชน`;
            subjects = ["การงานอาชีพ", "ศิลปะ", "สังคมศึกษา"];
            standards = ["ง 1.1", "ศ 2.1"];
            break;
          case "พิพิธภัณฑ์":
            name = `พิพิธภัณฑ์${core}`;
            description = `พิพิธภัณฑ์ท้องถิ่นของจังหวัด${province} แสดงประวัติศาสตร์ ภูมิปัญญา และวัฒนธรรมของคนในพื้นที่`;
            subjects = ["ประวัติศาสตร์", "ศิลปะ", "สังคมศึกษา"];
            standards = ["ส 4.3"];
            break;
          default:
            name = `แหล่งเรียนรู้ชุมชน${core}`;
            description = `แหล่งเรียนรู้ท้องถิ่นของจังหวัด${province}`;
            subjects = ["สังคมศึกษา"];
            standards = [];
        }

        return {
          id: `auto-${province}-${type}-${index}`,
          name,
          province,
          district,
          type,
          description,
          subjects,
          standards,
          tags
        };
      }

      function buildAutoAttractions() {
        const list = [];
        PROVINCES.forEach((province, pIndex) => {
          const district = defaultDistrictForProvince(province);
          ATTRACTION_TYPES.forEach((type, tIndex) => {
            const idx = pIndex * ATTRACTION_TYPES.length + tIndex;
            list.push(createGenericAttraction(province, district, type, idx));
          });
        });
        return list;
      }

      const AUTO_ATTRACTIONS = buildAutoAttractions();
      const ALL_ATTRACTIONS = [...BASE_ATTRACTIONS, ...AUTO_ATTRACTIONS];

      // --------- fallback เฉพาะจังหวัด/อำเภอกรณีหาไม่เจอ ----------
      function createFallbackResources(province, district) {
        const now = Date.now();
        return [
          {
            id: `fb-temple-${province}-${district}-${now}`,
            name: `วัดประจำชุมชน${district}`,
            province,
            district,
            type: "วัด",
            description: `วัดประจำชุมชนในอำเภอ${district} จังหวัด${province} เป็นศูนย์กลางกิจกรรมทางศาสนาและวัฒนธรรมของคนในพื้นที่`,
            subjects: [
              "สังคมศึกษา ศาสนา และวัฒนธรรม",
              "ประวัติศาสตร์ท้องถิ่น"
            ],
            standards: ["ส 1.1", "ส 1.2"],
            tags: ["วัด", "ชุมชน", "ศาสนา"]
          }
        ];
      }

      function createFallbackProvinceResource(province) {
        const core = normalizeProvinceCoreName(province);
        return [
          {
            id: `fb-city-${province}`,
            name: `ศาลหลักเมือง${core}`,
            province,
            district: `เมือง${core}`,
            type: "วัด",
            description: `สิ่งศักดิ์สิทธิ์คู่บ้านคู่เมืองของจังหวัด${province} ศูนย์รวมศรัทธาและประวัติศาสตร์ของผู้คนในพื้นที่`,
            subjects: ["ประวัติศาสตร์", "สังคมศึกษา"],
            standards: ["ส 4.3"],
            tags: ["ศาลหลักเมือง", "สถานที่สำคัญ"]
          }
        ];
      }

      // --------- การ render ผลลัพธ์ ----------
      function renderResults(resources, hasSearched, province, district) {
        const initialState = document.getElementById("initialState");
        const resultsList = document.getElementById("resultsList");

        if (!hasSearched) {
          initialState.classList.remove("hidden");
          resultsList.classList.add("hidden");
          resultsList.innerHTML = "";
          return;
        }

        initialState.classList.add("hidden");
        resultsList.classList.remove("hidden");
        resultsList.innerHTML = "";

        if (!province) {
          resultsList.innerHTML =
            '<div class="rounded-2xl bg-white border border-red-100 p-4 text-sm text-red-600">โปรดเลือกจังหวัดก่อนทำการค้นหา</div>';
          return;
        }

        if (!resources || resources.length === 0) {
          resultsList.innerHTML =
            '<div class="rounded-2xl bg-white border border-yellow-100 p-4 text-sm text-yellow-700">ไม่พบแหล่งเรียนรู้ / แหล่งท่องเที่ยวที่ตรงกับเงื่อนไขที่ค้นหา</div>';
          return;
        }

        const headerText = district
          ? `ผลการค้นหาในจังหวัด${province} (อำเภอ ${district})`
          : `ตัวอย่างแหล่งเรียนรู้ / แหล่งท่องเที่ยวทุกประเภทในจังหวัด${province}`;

        const header = document.createElement("div");
        header.className = "flex items-center justify-between mb-1";
        header.innerHTML = `
          <h3 class="text-sm sm:text-base font-semibold text-gray-900">${headerText}</h3>
          <p class="text-[11px] text-gray-500">${resources.length} แห่ง</p>
        `;
        resultsList.appendChild(header);

        const grid = document.createElement("div");
        grid.className =
          "grid gap-4 sm:grid-cols-2 lg:grid-cols-3 items-stretch";
        resultsList.appendChild(grid);

        resources.forEach((item) => {
          const card = document.createElement("article");
          card.className =
            "bg-white rounded-2xl border border-gray-100 shadow-sm flex flex-col overflow-hidden";

          const body = document.createElement("div");
          body.className = "p-4 flex-1 flex flex-col";

          const locationBadge = `
            <div class="flex items-center gap-2 mb-1">
              <span class="inline-flex items-center px-2 py-0.5 rounded-full bg-thai-accent text-thai-primary text-[10px] font-medium">
                ${item.province}
              </span>
              <span class="text-[11px] text-gray-500">อำเภอ ${item.district}</span>
            </div>
          `;

          const subjects =
            item.subjects && item.subjects.length
              ? item.subjects.join(" · ")
              : "-";

          const standards =
            item.standards && item.standards.length
              ? item.standards.join(", ")
              : "-";

          const tags =
            item.tags && item.tags.length
              ? item.tags
              : ["แหล่งเรียนรู้ชุมชน"];

          const typeLabel = item.type || "-";

          body.innerHTML = `
            ${locationBadge}
            <h4 class="text-sm font-semibold text-gray-900 mb-1 line-clamp-2">
              ${item.name}
            </h4>
            <p class="text-[11px] text-thai-primary font-medium mb-1">
              ประเภทแหล่งเรียนรู้/ท่องเที่ยว: <span class="font-semibold">${typeLabel}</span>
            </p>
            <p class="text-xs text-gray-600 mb-3 line-clamp-4">
              ${item.description}
            </p>
            <div class="mt-auto space-y-2">
              <div class="flex flex-col gap-1">
                <p class="text-[11px] text-gray-500">
                  กลุ่มสาระที่เกี่ยวข้อง:
                  <span class="text-gray-800">${subjects}</span>
                </p>
                <p class="text-[11px] text-gray-500">
                  ตัวชี้วัด / มาตรฐาน:
                  <span class="text-gray-800">${standards}</span>
                </p>
              </div>
              <div class="flex flex-wrap gap-1 mt-1">
                ${tags
                  .map(
                    (tag) =>
                      `<span class="inline-flex items-center px-2 py-0.5 rounded-full bg-gray-100 text-gray-700 text-[10px]">#${tag}</span>`
                  )
                  .join("")}
              </div>
            </div>
          `;

          card.appendChild(body);
          grid.appendChild(card);
        });
      }

      // --------- การทำงานเมื่อ DOM โหลดเสร็จ ----------
      document.addEventListener("DOMContentLoaded", () => {
        const provinceSelect = document.getElementById("province");
        const districtInput = document.getElementById("district");
        const form = document.getElementById("searchForm");

        // เติมจังหวัดลงใน <select>
        PROVINCES.slice()
          .sort()
          .forEach((prov) => {
            const option = document.createElement("option");
            option.value = prov;
            option.textContent = prov;
            provinceSelect.appendChild(option);
          });

        let hasSearched = false;

        form.addEventListener("submit", (event) => {
          event.preventDefault();

          const province = provinceSelect.value.trim();
          const district = districtInput.value.trim();

          hasSearched = true;

          if (!province) {
            renderResults([], hasSearched, province, district);
            return;
          }

          // ฟิลเตอร์จาก ALL_ATTRACTIONS
          let filtered = ALL_ATTRACTIONS.filter((item) => {
            const matchProvince = item.province === province;
            const matchDistrict = district
              ? item.district.toLowerCase().includes(district.toLowerCase())
              : true;
            return matchProvince && matchDistrict;
          });

          if (filtered.length === 0 && district) {
            filtered = createFallbackResources(province, district);
          } else if (filtered.length === 0 && !district) {
            filtered = createFallbackProvinceResource(province);
          }

          renderResults(filtered, hasSearched, province, district);
        });

        // แสดงสถานะเริ่มต้น
        renderResults([], false, "", "");
      });
    </script>
  </body>
</html>
