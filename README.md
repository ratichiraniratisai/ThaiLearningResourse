<html lang="th">
<head>
  <meta charset="UTF-8" />
  <meta
    name="viewport"
    content="width=device-width, initial-scale=1.0"
  />
  <title>ระบบฐานข้อมูลแหล่งเรียนรู้ท้องถิ่น</title>

  <!-- TailwindCSS CDN -->
  <script src="https://cdn.tailwindcss.com"></script>

  <!-- ฟอนต์ Sarabun -->
  <link
    href="https://fonts.googleapis.com/css2?family=Sarabun:wght@300;400;500;600;700&display=swap"
    rel="stylesheet"
  />

  <!-- กำหนดธีมสี/ฟอนต์ -->
  <script>
    tailwind.config = {
      theme: {
        extend: {
          fontFamily: {
            sans: ["Sarabun", "sans-serif"],
          },
          colors: {
            "thai-primary": "#00695c", // Teal 800
            "thai-secondary": "#ffca28", // Amber 400
            "thai-accent": "#e0f2f1", // Teal 50
            "ministry-orange": "#f57c00",
          },
        },
      },
    };
  </script>

  <style>
    body {
      font-family: "Sarabun", sans-serif;
      background-color: #f3f4f6;
    }
  </style>
</head>
<body class="min-h-screen flex flex-col bg-gray-50">
  <!-- Header -->
  <header class="bg-thai-primary shadow-lg text-white sticky top-0 z-50">
    <div
      class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-4 flex flex-col md:flex-row items-center justify-between"
    >
      <div class="flex items-center space-x-4">
        <div
          class="bg-white/10 p-2.5 rounded-lg backdrop-blur-sm border border-white/20"
        >
          <svg
            xmlns="http://www.w3.org/2000/svg"
            class="h-8 w-8 text-thai-secondary"
            fill="none"
            viewBox="0 0 24 24"
            stroke="currentColor"
          >
            <path d="M12 14l9-5-9-5-9 5 9 5z" />
            <path
              d="M12 14l6.16-3.422a12.083 12.083 0 01.665 6.479A11.952 11.952 0 0012 20.055a11.952 11.952 0 00-6.824-2.998 12.078 12.078 0 01.665-6.479L12 14z"
            />
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M12 14l9-5-9-5-9 5 9 5zm0 0l6.16-3.422a12.083 12.083 0 01.665 6.479A11.952 11.952 0 0012 20.055a11.952 11.952 0 00-6.824-2.998 12.078 12.078 0 01.665-6.479L12 14zm-4 6v-7.5l4-2.222"
            />
          </svg>
        </div>
        <div>
          <h1 class="text-xl md:text-2xl font-bold leading-tight">
            ระบบฐานข้อมูลแหล่งเรียนรู้ท้องถิ่น
          </h1>
          <p class="text-sm text-teal-100 font-medium opacity-90">
            เชื่อมโยงมาตรฐาน/ตัวชี้วัด หลักสูตรแกนกลางการศึกษาขั้นพื้นฐาน
          </p>
        </div>
      </div>
    </div>
  </header>

  <!-- Main -->
  <main
    class="flex-grow max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-8 w-full"
  >
    <!-- ฟอร์มค้นหา -->
    <section
      class="bg-white rounded-xl shadow-md border border-gray-200 p-6 mb-8"
    >
      <h2 class="text-lg font-semibold text-gray-800 mb-4">
        ค้นหาแหล่งเรียนรู้ท้องถิ่น
      </h2>

      <div
        class="grid grid-cols-1 md:grid-cols-3 gap-4 items-end"
      >
        <!-- จังหวัด -->
        <div>
          <label
            for="province"
            class="block text-sm font-medium text-gray-700 mb-1"
            >จังหวัด</label
          >
          <select
            id="province"
            class="mt-1 block w-full rounded-lg border-gray-300 shadow-sm focus:ring-thai-primary focus:border-thai-primary text-sm"
          >
            <option value="">-- เลือกจังหวัด --</option>
          </select>
        </div>

        <!-- อำเภอ/เขต -->
        <div>
          <label
            for="district"
            class="block text-sm font-medium text-gray-700 mb-1"
            >อำเภอ/เขต</label
          >
          <select
            id="district"
            class="mt-1 block w-full rounded-lg border-gray-300 shadow-sm focus:ring-thai-primary focus:border-thai-primary text-sm"
            disabled
          >
            <option value="">-- เลือกอำเภอ/เขต --</option>
          </select>
        </div>

        <!-- ปุ่มค้นหา -->
        <div class="flex md:justify-end">
          <button
            id="searchBtn"
            class="inline-flex items-center justify-center w-full md:w-auto px-6 py-2.5 rounded-lg bg-thai-primary text-white text-sm font-medium shadow hover:bg-emerald-700 transition"
          >
            <svg
              class="h-4 w-4 mr-2"
              fill="none"
              viewBox="0 0 24 24"
              stroke="currentColor"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                d="M8 16l4-4-4-4m5 8h3a2 2 0 002-2V6a2 2 0 00-2-2h-3"
              />
            </svg>
            ค้นหา
          </button>
        </div>
      </div>
      <p class="text-xs text-gray-500 mt-3">
        * รายชื่ออำเภอ/เขต และแหล่งเรียนรู้เป็นตัวอย่างที่ใช้ชื่อสถานที่จริง สามารถเพิ่ม-แก้ไขให้ครบถ้วนตามบริบทของจังหวัด/อำเภอได้
      </p>
    </section>

    <!-- พื้นที่แสดงผล -->
    <section id="resultsContainer">
      <!-- จะถูกเติมด้วย JavaScript -->
    </section>

    <!-- สถานะเริ่มต้น (ก่อนค้นหา) -->
    <section
      id="initialState"
      class="text-center py-20 px-4"
    >
      <h2
        class="text-3xl md:text-4xl font-bold text-gray-800 mb-6 tracking-tight"
      >
        ค้นหาแหล่งเรียนรู้
        <span class="text-thai-primary">ใกล้ตัวคุณ</span>
      </h2>
      <p
        class="text-gray-600 max-w-2xl mx-auto text-lg leading-relaxed"
      >
        ระบบตัวอย่างนี้ช่วยให้ครูและนักเรียนสามารถสำรวจแหล่งเรียนรู้ในชุมชน
        และเชื่อมโยงกับสาระการเรียนรู้/มาตรฐานของหลักสูตรแกนกลางฯ
        เพื่อออกแบบการเรียนรู้ที่สอดคล้องกับบริบทพื้นที่
      </p>
    </section>
  </main>

  <!-- Footer -->
  <footer
    class="bg-gray-800 text-gray-400 py-8 mt-auto border-t border-gray-700"
  >
    <div class="max-w-7xl mx-auto px-4 text-center">
      <p class="text-sm font-light">
        ©
        <span id="yearSpan"></span>
        ระบบฐานข้อมูลแหล่งเรียนรู้ท้องถิ่นเพื่อการศึกษาไทย
      </p>
      <p class="text-xs text-gray-500 mt-2">
        ตัวอย่างเว็บสำหรับใช้งานบน GitHub Pages (Static HTML + TailwindCSS + Vanilla JS)
      </p>
    </div>
  </footer>

  <!-- JavaScript ส่วนการทำงาน -->
  <script>
    // -------------------------------
    // 1) ข้อมูลจังหวัด + อำเภอ/เขต (ตัวอย่างจำนวนมาก เพิ่มเองได้)
    // -------------------------------
    const PROVINCE_DISTRICTS = {
      "กรุงเทพมหานคร": [
        "พระนคร","ดุสิต","หนองจอก","บางรัก","บางเขน","บางกะปิ","ปทุมวัน",
        "ป้อมปราบศัตรูพ่าย","พระโขนง","มีนบุรี","ลาดกระบัง","ยานนาวา",
        "สัมพันธวงศ์","พญาไท","ธนบุรี","บางกอกใหญ่","ห้วยขวาง","คลองสาน",
        "ตลิ่งชัน","บางกอกน้อย","บางขุนเทียน","ภาษีเจริญ","หนองแขม","ราษฎร์บูรณะ",
        "บางพลัด","ดินแดง","บึงกุ่ม","สาทร","บางซื่อ","จตุจักร","บางคอแหลม",
        "ประเวศ","คลองเตย","สวนหลวง","จอมทอง","ดอนเมือง","ราชเทวี","ลาดพร้าว",
        "วัฒนา","บางแค","หลักสี่","สายไหม","คันนายาว","สะพานสูง","วังทองหลาง",
        "คลองสามวา","บางนา","ทวีวัฒนา","ทุ่งครุ","บางบอน"
      ],
      "เชียงใหม่": [
        "เมืองเชียงใหม่","จอมทอง","แม่แจ่ม","เชียงดาว","ดอยสะเก็ด","แม่แตง",
        "แม่ริม","สะเมิง","ฝาง","แม่อาย","พร้าว","สันป่าตอง","สันกำแพง",
        "สันทราย","หางดง","ฮอด","ดอยเต่า","อมก๋อย","สารภี","เวียงแหง",
        "ไชยปราการ","แม่วาง","แม่ออน","ดอยหล่อ","กัลยาณิวัฒนา"
      ],
      "เชียงราย": [
        "เมืองเชียงราย","เวียงชัย","เชียงของ","เทิง","พาน","ป่าแดด","แม่จัน",
        "เชียงแสน","แม่สาย","แม่สรวย","เวียงป่าเป้า","พญาเม็งราย","เวียงเชียงรุ้ง",
        "เวียงแก่น","ขุนตาล","แม่ฟ้าหลวง","แม่ลาว","เวียงเชียงของ","ดอยหลวง"
      ],
      "ภูเก็ต": [
        "เมืองภูเก็ต","กะทู้","ถลาง"
      ],
      "ชลบุรี": [
        "เมืองชลบุรี","บ้านบึง","หนองใหญ่","บางละมุง","พานทอง","พนัสนิคม",
        "ศรีราชา","เกาะสีชัง","สัตหีบ","บ่อทอง","เกาะจันทร์"
      ],
      "กาญจนบุรี": [
        "เมืองกาญจนบุรี","ไทรโยค","บ่อพลอย","ศรีสวัสดิ์","ท่ามะกา","ท่าม่วง",
        "ทองผาภูมิ","สังขละบุรี","พนมทวน","เลาขวัญ","ด่านมะขามเตี้ย","หนองปรือ","ห้วยกระเจา"
      ],
      "ประจวบคีรีขันธ์": [
        "เมืองประจวบคีรีขันธ์","กุยบุรี","ทับสะแก","บางสะพาน","บางสะพานน้อย","ปราณบุรี","หัวหิน","สามร้อยยอด"
      ],
      "สุรินทร์": [
        "เมืองสุรินทร์","ชุมพลบุรี","ท่าตูม","จอมพระ","ปราสาท","กาบเชิง","รัตนบุรี",
        "สนม","ศีขรภูมิ","สังขะ","ลำดวน","สำโรงทาบ","บัวเชด","พนมดงรัก","ศรีณรงค์","เขวาสินรินทร์","โนนนารายณ์"
      ],
      "กระบี่": [
        "เมืองกระบี่","เขาพนม","เขาล้าง","คลองท่อม","อ่าวลึก","ปลายพระยา","ลำทับ","เหนือคลอง"
      ],
      "ราชบุรี": [
        "เมืองราชบุรี","จอมบึง","สวนผึ้ง","ดำเนินสะดวก","บ้านโป่ง","บางแพ","โพธาราม","ปากท่อ","วัดเพลง","บ้านคา"
      ],
      // --- ตัวอย่างจังหวัดอื่น ๆ (เพิ่มเองได้ในรูปแบบเดียวกัน) ---
      "นครราชสีมา": [
        "เมืองนครราชสีมา","ครบุรี","เสิงสาง","คง","บ้านเหลื่อม","จักราช",
        "โชคชัย","ด่านขุนทด","โนนไทย","โนนสูง","ขามสะแกแสง","บัวใหญ่","ประทาย",
        "ปักธงชัย","พิมาย","ห้วยแถลง","ชุมพวง","สูงเนิน","ขามทะเลสอ","สีคิ้ว",
        "ปากช่อง","หนองบุนนาก","แก้งสนามนาง","โนนแดง","วังน้ำเขียว","เทพารักษ์",
        "เมืองยาง","พระทองคำ","ลำทะเมนชัย","บัวลาย","สีดา","เฉลิมพระเกียรติ"
      ]
      // หมายเหตุ: ถ้าต้องการให้ครบทุกจังหวัด ให้เพิ่ม key/array ตามรูปแบบนี้
    };

    // รายชื่อจังหวัด (ใช้ key ของ PROVINCE_DISTRICTS ถ้ามี ไม่มีก็เพิ่มเอง)
    const THAI_PROVINCES = [
      "กรุงเทพมหานคร",
      "กระบี่",
      "กาญจนบุรี",
      "ขอนแก่น",
      "จันทบุรี",
      "ฉะเชิงเทรา",
      "ชลบุรี",
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
      "พะเยา",
      "พังงา",
      "พัทลุง",
      "พิจิตร",
      "พิษณุโลก",
      "เพชรบุรี",
      "เพชรบูรณ์",
      "แพร่",
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
      "อำนาจเจริญ",
      "อุดรธานี",
      "อุตรดิตถ์",
      "อุทัยธานี",
      "อุบลราชธานี"
    ];

    // เติม options จังหวัดใน select
    const provinceSelect = document.getElementById("province");
    THAI_PROVINCES.forEach((p) => {
      const opt = document.createElement("option");
      opt.value = p;
      opt.textContent = p;
      provinceSelect.appendChild(opt);
    });

    const districtSelect = document.getElementById("district");

    // เมื่อเลือกจังหวัด ให้เติมลิสต์อำเภอ/เขต
    provinceSelect.addEventListener("change", () => {
      const province = provinceSelect.value;
      districtSelect.innerHTML = "";
      if (!province) {
        districtSelect.disabled = true;
        const opt = document.createElement("option");
        opt.value = "";
        opt.textContent = "-- เลือกอำเภอ/เขต --";
        districtSelect.appendChild(opt);
        return;
      }

      const districts = PROVINCE_DISTRICTS[province];
      districtSelect.disabled = false;

      const firstOpt = document.createElement("option");
      firstOpt.value = "";
      firstOpt.textContent = "ทุกอำเภอ/เขต";
      districtSelect.appendChild(firstOpt);

      if (districts && districts.length) {
        districts.forEach((d) => {
          const opt = document.createElement("option");
          opt.value = d;
          opt.textContent = d;
          districtSelect.appendChild(opt);
        });
      } else {
        // ถ้าไม่มีใน PROVINCE_DISTRICTS ให้สร้างชื่ออำเภอหลักแบบอัตโนมัติ
        const autoDistrict = province === "กรุงเทพมหานคร"
          ? "พระนคร"
          : `เมือง${province.replace("จังหวัด", "").trim()}`;
        const opt = document.createElement("option");
        opt.value = autoDistrict;
        opt.textContent = autoDistrict;
        districtSelect.appendChild(opt);
      }
    });

    // -------------------------------
    // 2) ข้อมูลแหล่งเรียนรู้/สถานที่ท่องเที่ยว (ใช้ชื่อจริง + ภาพตัวอย่าง)
    // -------------------------------
    const SAMPLE_RESOURCES = [
      // กรุงเทพฯ
      {
        id: "bkk-01",
        name: "วัดพระศรีรัตนศาสดาราม (วัดพระแก้ว)",
        province: "กรุงเทพมหานคร",
        district: "พระนคร",
        description:
          "พระอุโบสถประดิษฐานพระแก้วมรกต ศูนย์รวมศรัทธาและแหล่งเรียนรู้ประวัติศาสตร์ ศิลปกรรม และสถาปัตยกรรมไทยในเขตเกาะรัตนโกสินทร์",
        subjects: ["สังคมศึกษา ศาสนาและวัฒนธรรม", "ประวัติศาสตร์", "ศิลปะ"],
        standards: ["ส 1.1", "ส 4.3", "ศ 1.1"],
        tags: ["วัด", "โบราณสถาน", "ประวัติศาสตร์ชาติไทย"],
        imageUrl:
          "https://images.pexels.com/photos/415960/pexels-photo-415960.jpeg"
      },
      {
        id: "bkk-02",
        name: "วัดโพธิ์ (วัดพระเชตุพนวิมลมังคลาราม)",
        province: "กรุงเทพมหานคร",
        district: "พระนคร",
        description:
          "พระวิหารพระพุทธไสยาสน์และศูนย์กลางการแพทย์แผนไทยดั้งเดิม เหมาะสำหรับบูรณาการสุขศึกษา ศิลปะ และประวัติศาสตร์",
        subjects: ["สุขศึกษา", "ศิลปะ", "สังคมศึกษา"],
        standards: ["พ 4.1", "ศ 1.1"],
        tags: ["วัด", "การแพทย์แผนไทย", "มรดกทางภูมิปัญญา"],
        imageUrl:
          "https://images.pexels.com/photos/247431/pexels-photo-247431.jpeg"
      },
      {
        id: "bkk-03",
        name: "ถนนคนเดินเยาวราช",
        province: "กรุงเทพมหานคร",
        district: "สัมพันธวงศ์",
        description:
          "ย่านไชน่าทาวน์ใจกลางกรุงเทพฯ แหล่งเรียนรู้วัฒนธรรมจีน การค้าชุมชน และเศรษฐกิจฐานรากผ่านอาหารและร้านค้าหลากหลาย",
        subjects: ["สังคมศึกษา", "การงานอาชีพ", "ภาษาไทย"],
        standards: ["ส 2.1", "ง 1.1"],
        tags: ["ถนนคนเดิน", "อาหาร", "ชุมชนชาวจีน"],
        imageUrl:
          "https://images.pexels.com/photos/1055755/pexels-photo-1055755.jpeg"
      },

      // เชียงใหม่
      {
        id: "cm-01",
        name: "วัดพระธาตุดอยสุเทพราชวรวิหาร",
        province: "เชียงใหม่",
        district: "เมืองเชียงใหม่",
        description:
          "ปูชนียสถานคู่เมืองเชียงใหม่ อยู่บนดอยสุเทพ สามารถมองเห็นภูมิประเทศโดยรอบ เหมาะสำหรับเรียนรู้ประวัติศาสตร์ วัฒนธรรมล้านนา และภูมิศาสตร์",
        subjects: ["สังคมศึกษา", "ภูมิศาสตร์", "ประวัติศาสตร์ท้องถิ่น"],
        standards: ["ส 1.1", "ส 5.1"],
        tags: ["วัด", "ดอย", "วัฒนธรรมล้านนา"],
        imageUrl:
          "https://images.pexels.com/photos/208732/pexels-photo-208732.jpeg"
      },
      {
        id: "cm-02",
        name: "ดอยอินทนนท์",
        province: "เชียงใหม่",
        district: "จอมทอง",
        description:
          "ยอดเขาที่สูงที่สุดในประเทศไทย แหล่งเรียนรู้เรื่องระบบนิเวศป่าดิบเขา ความหลากหลายทางชีวภาพ และการเปลี่ยนแปลงภูมิอากาศ",
        subjects: ["วิทยาศาสตร์", "ภูมิศาสตร์"],
        standards: ["ว 8.1", "ส 5.1"],
        tags: ["ดอย", "อุทยานแห่งชาติ", "ระบบนิเวศป่าดิบเขา"],
        imageUrl:
          "https://images.pexels.com/photos/417074/pexels-photo-417074.jpeg"
      },
      {
        id: "cm-03",
        name: "ถนนคนเดินท่าแพ",
        province: "เชียงใหม่",
        district: "เมืองเชียงใหม่",
        description:
          "ถนนคนเดินที่รวบรวมงานหัตถกรรม อาหาร และดนตรีพื้นเมืองล้านนา เป็นพื้นที่เรียนรู้เศรษฐกิจสร้างสรรค์และอัตลักษณ์ท้องถิ่น",
        subjects: ["การงานอาชีพ", "ศิลปะ", "สังคมศึกษา"],
        standards: ["ง 1.1", "ศ 2.1"],
        tags: ["ถนนคนเดิน", "งานหัตถกรรม", "วัฒนธรรมล้านนา"],
        imageUrl:
          "https://images.pexels.com/photos/258945/pexels-photo-258945.jpeg"
      },

      // เชียงราย
      {
        id: "cr-01",
        name: "วัดร่องขุ่น",
        province: "เชียงราย",
        district: "เมืองเชียงราย",
        description:
          "วัดที่ออกแบบโดยอาจารย์เฉลิมชัย โฆษิตพิพัฒน์ ใช้เป็นแหล่งเรียนรู้ศิลปะร่วมสมัย สัญลักษณ์ และแนวคิดพุทธศิลป์",
        subjects: ["ศิลปะ", "สังคมศึกษา"],
        standards: ["ศ 1.1"],
        tags: ["วัด", "ศิลปะร่วมสมัย", "สถาปัตยกรรม"],
        imageUrl:
          "https://images.pexels.com/photos/208701/pexels-photo-208701.jpeg"
      },
      {
        id: "cr-02",
        name: "ดอยตุงและพระตำหนักดอยตุง",
        province: "เชียงราย",
        district: "แม่ฟ้าหลวง",
        description:
          "พื้นที่โครงการพัฒนาดอยตุง แหล่งเรียนรู้เรื่องการฟื้นฟูป่า การพัฒนาคุณภาพชีวิตชุมชนบนพื้นที่สูง และเกษตรบนดอย",
        subjects: ["สังคมศึกษา", "การงานอาชีพ", "วิทยาศาสตร์"],
        standards: ["ส 2.1", "ง 1.1", "ว 8.1"],
        tags: ["ดอย", "โครงการพัฒนา", "เกษตรบนพื้นที่สูง"],
        imageUrl:
          "https://images.pexels.com/photos/356830/pexels-photo-356830.jpeg"
      },

      // ภูเก็ต
      {
        id: "pk-01",
        name: "หาดไม้ขาว",
        province: "ภูเก็ต",
        district: "ถลาง",
        description:
          "ชายหาดเงียบสงบทางตอนเหนือของเกาะภูเก็ต มีภูมิประเทศทรายละเอียดและคลื่นทะเล เหมาะสำหรับศึกษาระบบนิเวศชายฝั่งและการท่องเที่ยวเชิงอนุรักษ์",
        subjects: ["วิทยาศาสตร์", "สังคมศึกษา"],
        standards: ["ว 8.1", "ส 2.1"],
        tags: ["หาด", "ทะเล", "การท่องเที่ยวเชิงอนุรักษ์"],
        imageUrl:
          "https://images.pexels.com/photos/457882/pexels-photo-457882.jpeg"
      },
      {
        id: "pk-02",
        name: "พิพิธภัณฑ์ภูเก็ตไทยหัว",
        province: "ภูเก็ต",
        district: "เมืองภูเก็ต",
        description:
          "อาคารชิโนโปรตุกีสเก่าแก่จัดแสดงประวัติศาสตร์ภูเก็ตและชุมชนชาวจีนโพ้นทะเล เหมาะสำหรับเรียนรู้วัฒนธรรมและการตั้งถิ่นฐานของชุมชนเมืองท่า",
        subjects: ["ประวัติศาสตร์", "สังคมศึกษา", "ศิลปะ"],
        standards: ["ส 4.3"],
        tags: ["พิพิธภัณฑ์", "อาคารเก่า", "ชุมชนชาวจีน"],
        imageUrl:
          "https://images.pexels.com/photos/208602/pexels-photo-208602.jpeg"
      },

      // ชลบุรี
      {
        id: "cb-01",
        name: "หาดพัทยา",
        province: "ชลบุรี",
        district: "บางละมุง",
        description:
          "ชายหาดสำคัญของภาคตะวันออก แหล่งเรียนรู้เรื่องการท่องเที่ยว เศรษฐกิจบริการ และผลกระทบต่อสิ่งแวดล้อมชายฝั่ง",
        subjects: ["สังคมศึกษา", "การงานอาชีพ", "วิทยาศาสตร์"],
        standards: ["ส 2.1", "ง 1.1", "ว 8.1"],
        tags: ["หาด", "การท่องเที่ยว", "เศรษฐกิจบริการ"],
        imageUrl:
          "https://images.pexels.com/photos/258154/pexels-photo-258154.jpeg"
      },
      {
        id: "cb-02",
        name: "เขาชีจรรย์",
        province: "ชลบุรี",
        district: "สัตหีบ",
        description:
          "หน้าผาหินที่สลักเป็นพระพุทธรูปด้วยเลเซอร์ ขนาดใหญ่ ใช้เป็นแหล่งเรียนรู้ธรณีวิทยา ศิลปะ และศรัทธาทางศาสนา",
        subjects: ["วิทยาศาสตร์", "ศิลปะ", "สังคมศึกษา"],
        standards: ["ว 3.1", "ศ 1.1"],
        tags: ["ภูเขา", "ศิลปะบนหน้าผา", "แหล่งท่องเที่ยวสำคัญ"],
        imageUrl:
          "https://images.pexels.com/photos/417173/pexels-photo-417173.jpeg"
      },

      // กาญจนบุรี
      {
        id: "kn-01",
        name: "อุทยานแห่งชาติน้ำตกเอราวัณ",
        province: "กาญจนบุรี",
        district: "ศรีสวัสดิ์",
        description:
          "น้ำตกชั้นต่าง ๆ ในเขตอุทยานแห่งชาติ เหมาะสำหรับศึกษาระบบนิเวศป่า น้ำตก และการท่องเที่ยวเชิงอนุรักษ์",
        subjects: ["วิทยาศาสตร์", "ภูมิศาสตร์"],
        standards: ["ว 8.1"],
        tags: ["น้ำตก", "อุทยานแห่งชาติ", "ป่า"],
        imageUrl:
          "https://images.pexels.com/photos/460376/pexels-photo-460376.jpeg"
      },
      {
        id: "kn-02",
        name: "เขาช้างเผือก",
        province: "กาญจนบุรี",
        district: "ทองผาภูมิ",
        description:
          "เส้นทางเดินป่าบนสันเขา มีลักษณะสันคมมีด มองเห็นภูมิประเทศเขาสลับซับซ้อน เหมาะสำหรับเรียนรู้ภูมิประเทศและการท่องเที่ยวเชิงผจญภัยอย่างปลอดภัย",
        subjects: ["ภูมิศาสตร์", "วิทยาศาสตร์"],
        standards: ["ส 5.1", "ว 8.1"],
        tags: ["ภูเขา", "เดินป่า", "ท่องเที่ยวเชิงผจญภัย"],
        imageUrl:
          "https://images.pexels.com/photos/417142/pexels-photo-417142.jpeg"
      },

      // ประจวบคีรีขันธ์
      {
        id: "pkk-01",
        name: "อ่าวมะนาว",
        province: "ประจวบคีรีขันธ์",
        district: "เมืองประจวบคีรีขันธ์",
        description:
          "อ่าวโค้งรูปพระจันทร์ เป็นแหล่งท่องเที่ยวสำคัญ เหมาะสำหรับเรียนรู้ระบบนิเวศชายฝั่ง การประมง และเศรษฐกิจการท่องเที่ยวของชุมชน",
        subjects: ["วิทยาศาสตร์", "สังคมศึกษา", "การงานอาชีพ"],
        standards: ["ว 8.1", "ส 2.1"],
        tags: ["อ่าว", "ทะเล", "ชุมชนประมง"],
        imageUrl:
          "https://images.pexels.com/photos/994605/pexels-photo-994605.jpeg"
      },

      // กระบี่
      {
        id: "kb-01",
        name: "หาดไร่เลย์",
        province: "กระบี่",
        district: "เมืองกระบี่",
        description:
          "ชายหาดที่ล้อมรอบด้วยหน้าผาหินปูน เดินทางเข้าได้โดยทางเรือ เหมาะสำหรับศึกษาการท่องเที่ยวทางทะเลและกีฬาปีนผา",
        subjects: ["วิทยาศาสตร์", "สังคมศึกษา"],
        standards: ["ว 8.1", "ส 2.1"],
        tags: ["หาด", "ปีนผา", "ทะเล"],
        imageUrl:
          "https://images.pexels.com/photos/346885/pexels-photo-346885.jpeg"
      },
      {
        id: "kb-02",
        name: "อ่าวมาหยา (หมู่เกาะพีพี)",
        province: "กระบี่",
        district: "เมืองกระบี่",
        description:
          "อ่าวชื่อดังระดับโลก น้ำทะเลสีฟ้าใสและหาดทรายขาว เหมาะเป็นกรณีศึกษาเรื่องผลกระทบของการท่องเที่ยวต่อระบบนิเวศทางทะเล",
        subjects: ["วิทยาศาสตร์", "สังคมศึกษา"],
        standards: ["ว 8.1", "ส 2.1"],
        tags: ["อ่าว", "หมู่เกาะ", "การท่องเที่ยวทางทะเล"],
        imageUrl:
          "https://images.pexels.com/photos/994605/pexels-photo-994605.jpeg"
      },

      // สุรินทร์ – หมู่บ้านช้าง
      {
        id: "sn-01",
        name: "หมู่บ้านช้างบ้านตากลาง",
        province: "สุรินทร์",
        district: "ท่าตูม",
        description:
          "ชุมชนที่มีวัฒนธรรมการเลี้ยงช้างมายาวนาน เหมาะสำหรับเรียนรู้ภูมิปัญญาท้องถิ่น วิถีชีวิตชาวกูย และการจัดการการท่องเที่ยวเชิงวัฒนธรรม",
        subjects: ["สังคมศึกษา", "การงานอาชีพ"],
        standards: ["ส 2.1", "ง 1.1"],
        tags: ["หมู่บ้านช้าง", "ภูมิปัญญาท้องถิ่น", "วัฒนธรรม"],
        imageUrl:
          "https://images.pexels.com/photos/247431/pexels-photo-247431.jpeg"
      }

      // หมายเหตุ: สามารถเพิ่มวัด/น้ำตก/ภูเขา/ตลาด/ถนนคนเดิน ฯลฯ จังหวัดอื่น ๆ ต่อได้ในรูปแบบเดียวกัน
    ];

    // -------------------------------
    // 3) ฟังก์ชัน render การ์ดผลลัพธ์
    // -------------------------------
    const resultsContainer = document.getElementById("resultsContainer");
    const initialState = document.getElementById("initialState");

    function renderResults(items, province, district) {
      // ล้างของเดิม
      resultsContainer.innerHTML = "";

      if (!items) {
        initialState.classList.remove("hidden");
        return;
      }

      // ซ่อน initialState เมื่อกดค้นหา
      initialState.classList.add("hidden");

      if (items.length === 0) {
        const emptyBox = document.createElement("div");
        emptyBox.className =
          "text-center py-20 bg-white rounded-xl shadow-sm border border-dashed border-gray-300";
        emptyBox.innerHTML = `
          <div
            class="bg-gray-50 w-24 h-24 rounded-full flex items-center justify-center mx-auto mb-4"
          >
            <svg
              xmlns="http://www.w3.org/2000/svg"
              class="h-10 w-10 text-gray-400"
              fill="none"
              viewBox="0 0 24 24"
              stroke="currentColor"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="1"
                d="M19 11H5m14 0a2 2 0 012 2v6a2 2 0 01-2 2H5a2 2 0 01-2-2v-6a2 2 0 012-2m14 0V9a2 2 0 00-2-2M5 11V9a2 2 0 012-2m0 0V5a2 2 0 012-2h6a2 2 0 012 2v2M7 7h10"
              />
            </svg>
          </div>
          <p class="text-gray-600 text-lg font-medium">
            ยังไม่มีข้อมูลแหล่งเรียนรู้เฉพาะสำหรับอำเภอนี้
          </p>
          <p class="text-gray-400 text-sm mt-1">
            สามารถเพิ่มข้อมูลแหล่งเรียนรู้ของอำเภอ/จังหวัดนี้ในโค้ดส่วน SAMPLE_RESOURCES ได้
          </p>
        `;
        resultsContainer.appendChild(emptyBox);
        return;
      }

      const header = document.createElement("div");
      header.className =
        "flex items-center justify-between mb-6 flex-wrap gap-2";
      const sub = district
        ? `จังหวัด ${province} • อำเภอ/เขต ${district}`
        : `จังหวัด ${province}`;
      header.innerHTML = `
        <div>
          <h3
            class="text-lg font-semibold text-gray-700 border-l-4 border-thai-secondary pl-3"
          >
            ผลการค้นหาแหล่งเรียนรู้ ${
              district ? "ในพื้นที่" : "ในจังหวัด"
            }
          </h3>
          <p class="text-xs text-gray-500 mt-1">
            ${sub}
          </p>
        </div>
        <span
          class="text-xs text-gray-500 bg-white border border-gray-200 px-3 py-1 rounded-full shadow-sm"
        >
          พบทั้งหมด ${items.length} แห่ง
        </span>
      `;
      resultsContainer.appendChild(header);

      const grid = document.createElement("div");
      grid.className =
        "grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6";

      items.forEach((res) => {
        const card = document.createElement("article");
        card.className =
          "bg-white rounded-xl shadow-md border border-gray-200 overflow-hidden flex flex-col";

        const imgUrl =
          res.imageUrl ||
          `https://picsum.photos/seed/${encodeURIComponent(
            res.id
          )}/600/400`;

        card.innerHTML = `
          <div class="relative h-40 overflow-hidden">
            <img
              src="${imgUrl}"
              alt="${res.name}"
              class="w-full h-full object-cover"
            />
            <div class="absolute inset-0 bg-gradient-to-t from-black/60 to-transparent"></div>
            <div class="absolute bottom-2 left-3 right-3 flex justify-between items-end">
              <div>
                <p class="text-xs text-white/80">
                  จังหวัด ${res.province} • อำเภอ/เขต ${res.district}
                </p>
                <h4 class="font-semibold text-white text-sm line-clamp-2">
                  ${res.name}
                </h4>
              </div>
            </div>
          </div>
          <div class="p-4 flex flex-col gap-3 flex-grow">
            <p class="text-sm text-gray-700 leading-relaxed">
              ${res.description}
            </p>

            <div class="text-xs">
              <p class="font-semibold text-gray-700 mb-1">
                สาระการเรียนรู้ที่เกี่ยวข้อง:
              </p>
              <p class="text-gray-600">
                ${res.subjects.join(" • ")}
              </p>
            </div>

            <div class="text-xs">
              <p class="font-semibold text-gray-700 mb-1">
                มาตรฐาน/ตัวชี้วัด (ตัวอย่าง):
              </p>
              <ul class="list-disc list-inside text-gray-600 space-y-0.5">
                ${res.standards
                  .map((s) => `<li>${s}</li>`)
                  .join("")}
              </ul>
            </div>

            <div class="mt-1 flex flex-wrap gap-1.5">
              ${res.tags
                .map(
                  (t) =>
                    `<span class="inline-flex items-center px-2.5 py-0.5 rounded-full bg-thai-accent text-[11px] font-medium text-thai-primary border border-emerald-100">#${t}</span>`
                )
                .join("")}
            </div>
          </div>
        `;

        grid.appendChild(card);
      });

      resultsContainer.appendChild(grid);
    }

    // -------------------------------
    // 4) Logic เมื่อกดปุ่มค้นหา
    // -------------------------------
    document
      .getElementById("searchBtn")
      .addEventListener("click", () => {
        const province = document.getElementById("province").value.trim();
        const district = document
          .getElementById("district")
          .value.trim();

        if (!province) {
          alert("กรุณาเลือกจังหวัดก่อนทำการค้นหา");
          return;
        }

        // ฟิลเตอร์จาก SAMPLE_RESOURCES
        let filtered = SAMPLE_RESOURCES.filter((item) => {
          const matchProvince = item.province === province;
          const matchDistrict = district
            ? item.district === district
            : true;
          return matchProvince && matchDistrict;
        });

        renderResults(filtered, province, district);
      });

    // ปีใน footer
    document.getElementById("yearSpan").textContent =
      new Date().getFullYear();

    // แสดงสถานะเริ่มต้น
    renderResults(null);
  </script>
</body>
</html>

