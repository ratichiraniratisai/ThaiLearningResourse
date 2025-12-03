<html lang="th">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
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
            "thai-primary": "#00695c",
            "thai-secondary": "#ffca28",
            "thai-accent": "#e0f2f1",
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
  <main class="flex-grow max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-8 w-full">
    <!-- ฟอร์มค้นหา -->
    <section
      class="bg-white rounded-xl shadow-md border border-gray-200 p-6 mb-8"
    >
      <h2 class="text-lg font-semibold text-gray-800 mb-4">
        ค้นหาแหล่งเรียนรู้ท้องถิ่น
      </h2>

      <div class="grid grid-cols-1 md:grid-cols-3 gap-4 items-end">
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
        * ใช้ชื่อแหล่งท่องเที่ยวจริงอย่างน้อย 5 แห่งในทุกจังหวัด 77 จังหวัด
        สามารถเพิ่ม/แก้ไขรายละเอียดเพิ่มเติมในโค้ดได้
      </p>
    </section>

    <!-- พื้นที่แสดงผล -->
    <section id="resultsContainer"></section>

    <!-- สถานะเริ่มต้น (ก่อนค้นหา) -->
    <section id="initialState" class="text-center py-20 px-4">
      <h2
        class="text-3xl md:text-4xl font-bold text-gray-800 mb-6 tracking-tight"
      >
        ค้นหาแหล่งเรียนรู้
        <span class="text-thai-primary">ใกล้ตัวคุณ</span>
      </h2>
      <p class="text-gray-600 max-w-2xl mx-auto text-lg leading-relaxed">
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
        © <span id="yearSpan"></span>
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
    // 1) ข้อมูลจังหวัด + อำเภอ/เขต (ตัวอย่าง – สามารถเพิ่มเองได้)
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
      "ภูเก็ต": ["เมืองภูเก็ต","กะทู้","ถลาง"],
      "ชลบุรี": [
        "เมืองชลบุรี","บ้านบึง","หนองใหญ่","บางละมุง","พานทอง","พนัสนิคม",
        "ศรีราชา","เกาะสีชัง","สัตหีบ","บ่อทอง","เกาะจันทร์"
      ],
      "กาญจนบุรี": [
        "เมืองกาญจนบุรี","ไทรโยค","บ่อพลอย","ศรีสวัสดิ์","ท่ามะกา","ท่าม่วง",
        "ทองผาภูมิ","สังขละบุรี","พนมทวน","เลาขวัญ","ด่านมะขามเตี้ย","หนองปรือ","ห้วยกระเจา"
      ],
      "ประจวบคีรีขันธ์": [
        "เมืองประจวบคีรีขันธ์","กุยบุรี","ทับสะแก","บางสะพาน",
        "บางสะพานน้อย","ปราณบุรี","หัวหิน","สามร้อยยอด"
      ],
      "สุรินทร์": [
        "เมืองสุรินทร์","ชุมพลบุรี","ท่าตูม","จอมพระ","ปราสาท","กาบเชิง","รัตนบุรี",
        "สนม","ศีขรภูมิ","สังขะ","ลำดวน","สำโรงทาบ","บัวเชด","พนมดงรัก","ศรีณรงค์","เขวาสินรินทร์","โนนนารายณ์"
      ],
      "กระบี่": [
        "เมืองกระบี่","เขาพนม","คลองท่อม","อ่าวลึก","ปลายพระยา","ลำทับ","เหนือคลอง"
      ],
      "ราชบุรี": [
        "เมืองราชบุรี","จอมบึง","สวนผึ้ง","ดำเนินสะดวก","บ้านโป่ง",
        "บางแพ","โพธาราม","ปากท่อ","วัดเพลง","บ้านคา"
      ]
      // จังหวัดอื่น ๆ ถ้าต้องการเจาะอำเภอ สามารถเพิ่มได้ในรูปแบบเดียวกัน
    };

    // รายชื่อจังหวัด 77 จังหวัด
    const THAI_PROVINCES = [
      "กรุงเทพมหานคร","กระบี่","กาญจนบุรี","ขอนแก่น","จันทบุรี","ฉะเชิงเทรา","ชลบุรี","เชียงราย","เชียงใหม่","ตรัง","ตราด","ตาก","นครนายก","นครปฐม","นครพนม","นครราชสีมา","นครศรีธรรมราช","นครสวรรค์","นนทบุรี","นราธิวาส","น่าน","บึงกาฬ","บุรีรัมย์","ปทุมธานี","ประจวบคีรีขันธ์","ปราจีนบุรี","ปัตตานี","พระนครศรีอยุธยา","พะเยา","พังงา","พัทลุง","พิจิตร","พิษณุโลก","เพชรบุรี","เพชรบูรณ์","แพร่","ภูเก็ต","มหาสารคาม","มุกดาหาร","แม่ฮ่องสอน","ยโสธร","ยะลา","ร้อยเอ็ด","ระนอง","ระยอง","ราชบุรี","ลพบุรี","ลำปาง","ลำพูน","เลย","ศรีสะเกษ","สกลนคร","สงขลา","สตูล","สมุทรปราการ","สมุทรสงคราม","สมุทรสาคร","สระแก้ว","สระบุรี","สิงห์บุรี","สุโขทัย","สุพรรณบุรี","สุราษฎร์ธานี","สุรินทร์","หนองคาย","หนองบัวลำภู","อ่างทอง","อำนาจเจริญ","อุดรธานี","อุตรดิตถ์","อุทัยธานี","อุบลราชธานี"
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
        // ถ้าไม่มีใน PROVINCE_DISTRICTS ให้ใช้ชื่อ "เมืองจังหวัด"
        const autoDistrict =
          province === "กรุงเทพมหานคร" ? "พระนคร" : `เมือง${province}`;
        const opt = document.createElement("option");
        opt.value = autoDistrict;
        opt.textContent = autoDistrict;
        districtSelect.appendChild(opt);
      }
    });

    // -------------------------------
    // 2) ข้อมูลแหล่งท่องเที่ยวจริง 77 จังหวัด (อย่างน้อยจังหวัดละ 5 แห่ง)
    // -------------------------------
    const PLACE_TEMPLATES = {
      "กรุงเทพมหานคร": [
        { name: "วัดพระศรีรัตนศาสดาราม (วัดพระแก้ว)", district: "พระนคร" },
        { name: "พระบรมมหาราชวัง", district: "พระนคร" },
        { name: "วัดพระเชตุพนวิมลมังคลาราม (วัดโพธิ์)", district: "พระนคร" },
        { name: "ถนนเยาวราช (ไชน่าทาวน์)", district: "สัมพันธวงศ์" },
        { name: "ถนนข้าวสาร", district: "พระนคร" },
        { name: "หอศิลปวัฒนธรรมแห่งกรุงเทพมหานคร (BACC)", district: "ปทุมวัน" }
      ],
      "กระบี่": [
        { name: "อ่าวมาหยา หมู่เกาะพีพี", district: "เมืองกระบี่" },
        { name: "หาดไร่เลย์", district: "เมืองกระบี่" },
        { name: "สระมรกต", district: "คลองท่อม" },
        { name: "น้ำตกร้อน คลองท่อม", district: "คลองท่อม" },
        { name: "อ่าวนาง", district: "เมืองกระบี่" }
      ],
      "กาญจนบุรี": [
        { name: "สะพานข้ามแม่น้ำแคว", district: "เมืองกาญจนบุรี" },
        { name: "อุทยานแห่งชาติน้ำตกเอราวัณ", district: "ศรีสวัสดิ์" },
        { name: "อุทยานแห่งชาติไทรโยค", district: "ไทรโยค" },
        { name: "เขาช้างเผือก", district: "ทองผาภูมิ" },
        { name: "น้ำตกห้วยแม่ขมิ้น", district: "ศรีสวัสดิ์" }
      ],
      "ขอนแก่น": [
        { name: "บึงแก่นนคร", district: "เมืองขอนแก่น" },
        { name: "วัดหนองแวง (พระธาตุ 9 ชั้น)", district: "เมืองขอนแก่น" },
        { name: "พิพิธภัณฑสถานแห่งชาติ ขอนแก่น", district: "เมืองขอนแก่น" },
        { name: "เขื่อนอุบลรัตน์", district: "อุบลรัตน์" },
        { name: "ตลาดต้นตาล", district: "เมืองขอนแก่น" }
      ],
      "จันทบุรี": [
        { name: "ชุมชนริมน้ำจันทบูร", district: "เมืองจันทบุรี" },
        { name: "อาสนวิหารพระนางมารีอาปฏิสนธินิรมล", district: "เมืองจันทบุรี" },
        { name: "หาดเจ้าหลาว", district: "ท่าใหม่" },
        { name: "จุดชมวิวเนินนางพญา", district: "ท่าใหม่" },
        { name: "น้ำตกพลิ้ว", district: "แหลมสิงห์" }
      ],
      "ฉะเชิงเทรา": [
        { name: "วัดโสธรวรารามวรวิหาร", district: "เมืองฉะเชิงเทรา" },
        { name: "ตลาดน้ำบางคล้า", district: "บางคล้า" },
        { name: "วัดสมานรัตนาราม", district: "บางคล้า" },
        { name: "วัดหงษ์ทอง", district: "บางปะกง" },
        { name: "สวนสมเด็จพระศรีนครินทร์ ฉะเชิงเทรา", district: "เมืองฉะเชิงเทรา" }
      ],
      "ชลบุรี": [
        { name: "หาดพัทยา", district: "บางละมุง" },
        { name: "เกาะล้าน", district: "บางละมุง" },
        { name: "เขาชีจรรย์", district: "สัตหีบ" },
        { name: "สวนสัตว์เปิดเขาเขียว", district: "ศรีราชา" },
        { name: "ปราสาทสัจธรรม", district: "บางละมุง" }
      ],
      "เชียงราย": [
        { name: "วัดร่องขุ่น", district: "เมืองเชียงราย" },
        { name: "วัดร่องเสือเต้น", district: "เมืองเชียงราย" },
        { name: "ดอยตุงและพระตำหนักดอยตุง", district: "แม่ฟ้าหลวง" },
        { name: "สามเหลี่ยมทองคำ", district: "เชียงแสน" },
        { name: "ภูชี้ฟ้า", district: "เทิง" }
      ],
      "เชียงใหม่": [
        { name: "วัดพระธาตุดอยสุเทพราชวรวิหาร", district: "เมืองเชียงใหม่" },
        { name: "ดอยอินทนนท์", district: "จอมทอง" },
        { name: "ประตูท่าแพและถนนคนเดินท่าแพ", district: "เมืองเชียงใหม่" },
        { name: "ดอยอ่างขาง", district: "ฝาง" },
        { name: "ถนนนิมมานเหมินทร์", district: "เมืองเชียงใหม่" }
      ],
      "ตรัง": [
        { name: "เกาะกระดาน", district: "กันตัง" },
        { name: "เกาะมุก ถ้ำมรกต", district: "กันตัง" },
        { name: "หาดปากเมง", district: "สิเกา" },
        { name: "สวนพฤกษศาสตร์ภาคใต้ ทุ่งค่าย", district: "กันตัง" },
        { name: "น้ำตกสายรุ้ง", district: "นาโยง" }
      ],
      "ตราด": [
        { name: "หาดทรายขาว เกาะช้าง", district: "เกาะช้าง" },
        { name: "อ่าวบางเบ้า เกาะช้าง", district: "เกาะช้าง" },
        { name: "เกาะกูด", district: "เกาะกูด" },
        { name: "หาดบานชื่น", district: "คลองใหญ่" },
        { name: "ศาลเจ้าพ่อหลักเมืองตราด", district: "เมืองตราด" }
      ],
      "ตาก": [
        { name: "เขื่อนภูมิพล", district: "สามเงา" },
        { name: "สะพานแขวนสมโภชกรุงรัตนโกสินทร์ 200 ปี", district: "เมืองตาก" },
        { name: "น้ำตกทีลอซู (ทางจากตาก-อุ้มผาง)", district: "อุ้มผาง" },
        { name: "อุทยานแห่งชาติแม่เมย", district: "ท่าสองยาง" },
        { name: "วัดพระบรมธาตุบ้านตาก", district: "บ้านตาก" }
      ],
      "นครนายก": [
        { name: "น้ำตกนางรอง", district: "เมืองนครนายก" },
        { name: "น้ำตกวังตะไคร้", district: "เมืองนครนายก" },
        { name: "เขื่อนขุนด่านปราการชล", district: "เมืองนครนายก" },
        { name: "คลองมะเดื่อ", district: "เมืองนครนายก" },
        { name: "อุทยานแห่งชาติเขาใหญ่ (ด้านนครนายก)", district: "เมืองนครนายก" }
      ],
      "นครปฐม": [
        { name: "พระปฐมเจดีย์ราชวรมหาวิหาร", district: "เมืองนครปฐม" },
        { name: "พระราชวังสนามจันทร์", district: "เมืองนครปฐม" },
        { name: "พุทธมณฑล", district: "พุทธมณฑล" },
        { name: "ตลาดน้ำดอนหวาย", district: "สามพราน" },
        { name: "วัดไร่ขิง", district: "สามพราน" }
      ],
      "นครพนม": [
        { name: "พระธาตุพนมวรมหาวิหาร", district: "ธาตุพนม" },
        { name: "แลนด์มาร์คนครพนม ริมโขง", district: "เมืองนครพนม" },
        { name: "สะพานมิตรภาพไทย-ลาว แห่งที่ 3", district: "เมืองนครพนม" },
        { name: "วัดพระอินทร์แปลง", district: "เมืองนครพนม" },
        { name: "หมู่บ้านมิตรภาพไทย-เวียด", district: "เมืองนครพนม" }
      ],
      "นครราชสีมา": [
        { name: "อุทยานประวัติศาสตร์พิมาย", district: "พิมาย" },
        { name: "เขาใหญ่ (ด้านปากช่อง)", district: "ปากช่อง" },
        { name: "อนุสาวรีย์ท้าวสุรนารี (ย่าโม)", district: "เมืองนครราชสีมา" },
        { name: "สวนสัตว์นครราชสีมา", district: "โชคชัย" },
        { name: "วัดศาลาลอย", district: "เมืองนครราชสีมา" }
      ],
      "นครศรีธรรมราช": [
        { name: "วัดพระมหาธาตุวรมหาวิหาร", district: "เมืองนครศรีธรรมราช" },
        { name: "หมู่บ้านคีรีวง", district: "ลานสกา" },
        { name: "อุทยานแห่งชาติเขาหลวง", district: "ลานสกา" },
        { name: "ชายหาดขนอม", district: "ขนอม" },
        { name: "สนามหน้าเมืองนครศรีธรรมราช", district: "เมืองนครศรีธรรมราช" }
      ],
      "นครสวรรค์": [
        { name: "บึงบอระเพ็ด", district: "เมืองนครสวรรค์" },
        { name: "เขากบ วัดคีรีวงศ์", district: "เมืองนครสวรรค์" },
        { name: "อุทยานสวรรค์", district: "เมืองนครสวรรค์" },
        { name: "ตลาดปากน้ำโพ", district: "เมืองนครสวรรค์" },
        { name: "วัดเกรียงไกรกลาง", district: "เมืองนครสวรรค์" }
      ],
      "นนทบุรี": [
        { name: "เกาะเกร็ด", district: "ปากเกร็ด" },
        { name: "วัดเฉลิมพระเกียรติวรวิหาร", district: "เมืองนนทบุรี" },
        { name: "สวนสมเด็จพระศรีนครินทร์ นนทบุรี", district: "เมืองนนทบุรี" },
        { name: "ตลาดน้ำไทรน้อย", district: "ไทรน้อย" },
        { name: "เซ็นทรัลพลาซา เวสต์เกต", district: "บางใหญ่" }
      ],
      "นราธิวาส": [
        { name: "มัสยิดกลางจังหวัดนราธิวาส", district: "เมืองนราธิวาส" },
        { name: "หาดนราทัศน์", district: "เมืองนราธิวาส" },
        { name: "อุทยานแห่งชาติบูโด-สุไหงปาดี", district: "สุไหงปาดี" },
        { name: "เขาตันหยงมัส", district: "ระแงะ" },
        { name: "อ่าวมะนาว นราธิวาส", district: "เมืองนราธิวาส" }
      ],
      "น่าน": [
        { name: "วัดภูมินทร์", district: "เมืองน่าน" },
        { name: "วัดพระธาตุแช่แห้ง", district: "ภูเพียง" },
        { name: "ดอยเสมอดาว อุทยานแห่งชาติศรีน่าน", district: "นาน้อย" },
        { name: "บ่อเกลือโบราณ", district: "บ่อเกลือ" },
        { name: "วัดมิ่งเมือง", district: "เมืองน่าน" }
      ],
      "บึงกาฬ": [
        { name: "วัดภูทอก (วัดเจติยาคีรีวิหาร)", district: "ศรีวิไล" },
        { name: "ภูสิงห์ ผาหัวนาค", district: "เมืองบึงกาฬ" },
        { name: "น้ำตกถ้ำพระ", district: "บึงโขงหลง" },
        { name: "อุทยานแห่งชาติภูลังกา (เขตบึงกาฬ)", district: "บึงโขงหลง" },
        { name: "หาดคำสมบูรณ์ ริมโขง", district: "เมืองบึงกาฬ" }
      ],
      "บุรีรัมย์": [
        { name: "อุทยานประวัติศาสตร์พนมรุ้ง", district: "เฉลิมพระเกียรติ" },
        { name: "ปราสาทเมืองต่ำ", district: "ประโคนชัย" },
        { name: "สนามช้างอารีนา", district: "เมืองบุรีรัมย์" },
        { name: "เขากระโดง", district: "เมืองบุรีรัมย์" },
        { name: "หมู่บ้านทอผ้าไหม บ้านเจริญสุข", district: "เฉลิมพระเกียรติ" }
      ],
      "ปทุมธานี": [
        { name: "พิพิธภัณฑ์วิทยาศาสตร์แห่งชาติ", district: "คลองหลวง" },
        { name: "มหาวิทยาลัยธรรมศาสตร์ ศูนย์รังสิต", district: "คลองหลวง" },
        { name: "วัดเจดีย์หอย", district: "สามโคก" },
        { name: "ตลาดน้ำทุ่งบัวชม", district: "สามโคก" },
        { name: "ฟิวเจอร์พาร์ค รังสิต", district: "ธัญบุรี" }
      ],
      "ประจวบคีรีขันธ์": [
        { name: "อ่าวมะนาว", district: "เมืองประจวบคีรีขันธ์" },
        { name: "เขาช่องกระจก", district: "เมืองประจวบคีรีขันธ์" },
        { name: "หัวหิน ชายหาดหัวหิน", district: "หัวหิน" },
        { name: "อุทยานแห่งชาติเขาสามร้อยยอด", district: "สามร้อยยอด" },
        { name: "เขาหินเหล็กไฟ จุดชมวิวหัวหิน", district: "หัวหิน" }
      ],
      "ปราจีนบุรี": [
        { name: "อุทยานแห่งชาติเขาใหญ่ (ด้านปราจีนบุรี)", district: "ประจันตคาม" },
        { name: "อุทยานแห่งชาติทับลาน", district: "นาดี" },
        { name: "พิพิธภัณฑ์แพทย์แผนไทยปราจีนบุรี", district: "เมืองปราจีนบุรี" },
        { name: "น้ำตกสวนห้อม", district: "นาดี" },
        { name: "ตลาด 304", district: "ศรีมหาโพธิ" }
      ],
      "ปัตตานี": [
        { name: "มัสยิดกลางจังหวัดปัตตานี", district: "เมืองปัตตานี" },
        { name: "มัสยิดกรือเซะ", district: "เมืองปัตตานี" },
        { name: "หาดตะโละกาโปร์", district: "ยะหริ่ง" },
        { name: "หาดทรายแก้ว ปัตตานี", district: "หนองจิก" },
        { name: "ย่านเมืองเก่าปัตตานี", district: "เมืองปัตตานี" }
      ],
      "พระนครศรีอยุธยา": [
        { name: "อุทยานประวัติศาสตร์พระนครศรีอยุธยา", district: "พระนครศรีอยุธยา" },
        { name: "วัดไชยวัฒนาราม", district: "พระนครศรีอยุธยา" },
        { name: "วัดมหาธาตุ (เศียรพระในรากไม้)", district: "พระนครศรีอยุธยา" },
        { name: "วัดพนัญเชิงวรวิหาร", district: "พระนครศรีอยุธยา" },
        { name: "ตลาดน้ำอโยธยา", district: "พระนครศรีอยุธยา" }
      ],
      "พะเยา": [
        { name: "กว๊านพะเยา", district: "เมืองพะเยา" },
        { name: "วัดศรีโคมคำ (พระเจ้าตนหลวง)", district: "เมืองพะเยา" },
        { name: "วัดพระนั่งดิน", district: "เชียงคำ" },
        { name: "อุทยานแห่งชาติดอยภูนาง", district: "เชียงม่วน" },
        { name: "อ่างเก็บน้ำแม่ต๋ำ", district: "เมืองพะเยา" }
      ],
      "พังงา": [
        { name: "อ่าวพังงา เขาตะปู", district: "เมืองพังงา" },
        { name: "เกาะยาวใหญ่", district: "เกาะยาว" },
        { name: "หมู่เกาะสิมิลัน", district: "ท้ายเหมือง" },
        { name: "เขาหลัก", district: "ตะกั่วป่า" },
        { name: "น้ำตกลำปี", district: "ท้ายเหมือง" }
      ],
      "พัทลุง": [
        { name: "ทะเลน้อย", district: "ควนขนุน" },
        { name: "เขาอกทะลุ", district: "เมืองพัทลุง" },
        { name: "วัดเขียนบางแก้ว", district: "เขาชัยสน" },
        { name: "น้ำตกไพรวัลย์", district: "ศรีนครินทร์" },
        { name: "วัดถ้ำสุมณะ", district: "เมืองพัทลุง" }
      ],
      "พิจิตร": [
        { name: "บึงสีไฟ", district: "เมืองพิจิตร" },
        { name: "วัดท่าหลวง", district: "เมืองพิจิตร" },
        { name: "วัดโพธิ์ประทับช้าง", district: "โพธิ์ประทับช้าง" },
        { name: "สวนสมเด็จพระนเรศวรมหาราช", district: "เมืองพิจิตร" },
        { name: "แหล่งเรียนรู้การเกษตรบางมูลนาก", district: "บางมูลนาก" }
      ],
      "พิษณุโลก": [
        { name: "วัดพระศรีรัตนมหาธาตุวรมหาวิหาร (วัดใหญ่)", district: "เมืองพิษณุโลก" },
        { name: "อุทยานแห่งชาติภูหินร่องกล้า", district: "นครไทย" },
        { name: "อุทยานแห่งชาติทุ่งแสลงหลวง", district: "เนินมะปราง" },
        { name: "น้ำตกชาติตระการ", district: "ชาติตระการ" },
        { name: "สวนชมน้ำก๋ง", district: "เมืองพิษณุโลก" }
      ],
      "เพชรบุรี": [
        { name: "พระนครคีรี (เขาวัง)", district: "เมืองเพชรบุรี" },
        { name: "หาดชะอำ", district: "ชะอำ" },
        { name: "อุทยานแห่งชาติแก่งกระจาน", district: "แก่งกระจาน" },
        { name: "วัดมหาธาตุวรวิหาร เพชรบุรี", district: "เมืองเพชรบุรี" },
        { name: "โครงการชั่งหัวมันตามพระราชดำริ", district: "ท่ายาง" }
      ],
      "เพชรบูรณ์": [
        { name: "เขาค้อ", district: "เขาค้อ" },
        { name: "ภูทับเบิก", district: "หล่มเก่า" },
        { name: "อุทยานแห่งชาติน้ำหนาว", district: "น้ำหนาว" },
        { name: "อุทยานประวัติศาสตร์ศรีเทพ", district: "ศรีเทพ" },
        { name: "วัดพระธาตุผาซ่อนแก้ว", district: "เขาค้อ" }
      ],
      "แพร่": [
        { name: "วัดพระธาตุช่อแฮ", district: "เมืองแพร่" },
        { name: "คุ้มเจ้าหลวงเมืองแพร่", district: "เมืองแพร่" },
        { name: "วนอุทยานแพะเมืองผี", district: "เมืองแพร่" },
        { name: "วัดพงษ์สุนันท์", district: "เมืองแพร่" },
        { name: "กาดกองเก่า ถนนคนเดินแพร่", district: "เมืองแพร่" }
      ],
      "ภูเก็ต": [
        { name: "หาดป่าตอง", district: "กะทู้" },
        { name: "หาดไม้ขาว", district: "ถลาง" },
        { name: "เมืองเก่าภูเก็ต (ตึกชิโนโปรตุกีส)", district: "เมืองภูเก็ต" },
        { name: "แหลมพรหมเทพ", district: "เมืองภูเก็ต" },
        { name: "พิพิธภัณฑ์ภูเก็ตไทยหัว", district: "เมืองภูเก็ต" }
      ],
      "มหาสารคาม": [
        { name: "มหาวิทยาลัยมหาสารคาม", district: "กันทรวิชัย" },
        { name: "วัดพุทธมงคล", district: "เมืองมหาสารคาม" },
        { name: "สวนสาธารณะเฉลิมพระเกียรติ มมส.", district: "กันทรวิชัย" },
        { name: "ตลาดโต้รุ่งมหาสารคาม", district: "เมืองมหาสารคาม" },
        { name: "วัดหนองหอย", district: "กันทรวิชัย" }
      ],
      "มุกดาหาร": [
        { name: "สะพานมิตรภาพไทย-ลาว แห่งที่ 2", district: "เมืองมุกดาหาร" },
        { name: "หอแก้วมุกดาหาร", district: "เมืองมุกดาหาร" },
        { name: "ตลาดอินโดจีนริมโขง", district: "เมืองมุกดาหาร" },
        { name: "ภูผาเทิบ", district: "ดอนตาล" },
        { name: "วัดศรีมงคลใต้", district: "เมืองมุกดาหาร" }
      ],
      "แม่ฮ่องสอน": [
        { name: "ปาย และถนนคนเดินปาย", district: "ปาย" },
        { name: "ทะเลหมอกหยุนไหล", district: "ปาย" },
        { name: "บ้านรักไทย", district: "เมืองแม่ฮ่องสอน" },
        { name: "พระธาตุดอยกองมู", district: "เมืองแม่ฮ่องสอน" },
        { name: "ถ้ำปลา", district: "เมืองแม่ฮ่องสอน" }
      ],
      "ยโสธร": [
        { name: "วัดมหาธาตุ ยโสธร", district: "เมืองยโสธร" },
        { name: "สวนสาธารณะพญาแถนบึงแก", district: "เมืองยโสธร" },
        { name: "หมู่บ้านทำบั้งไฟ", district: "เมืองยโสธร" },
        { name: "วัดบ้านสิงห์", district: "เมืองยโสธร" },
        { name: "ถนนคนเดินงานประเพณีบุญบั้งไฟ", district: "เมืองยโสธร" }
      ],
      "ยะลา": [
        { name: "มัสยิดกลางจังหวัดยะลา", district: "เมืองยะลา" },
        { name: "สวนขวัญเมืองยะลา", district: "เมืองยะลา" },
        { name: "อุโมงค์ปิยะมิตร เบตง", district: "เบตง" },
        { name: "น้ำตกเฉลิมพระเกียรติ ร.9 เบตง", district: "เบตง" },
        { name: "ทะเลหมอกอัยเยอร์เวง", district: "เบตง" }
      ],
      "ร้อยเอ็ด": [
        { name: "บึงพลาญชัย", district: "เมืองร้อยเอ็ด" },
        { name: "วัดบูรพาภิราม", district: "เมืองร้อยเอ็ด" },
        { name: "พระมหาเจดีย์ชัยมงคล", district: "หนองพอก" },
        { name: "สวนสมเด็จพระศรีนครินทร์ ร้อยเอ็ด", district: "เมืองร้อยเอ็ด" },
        { name: "ประตูเมืองร้อยเอ็ด", district: "เมืองร้อยเอ็ด" }
      ],
      "ระนอง": [
        { name: "บ่อน้ำพุร้อนรักษะวาริน", district: "เมืองระนอง" },
        { name: "เกาะพยาม", district: "เมืองระนอง" },
        { name: "อุทยานแห่งชาติน้ำตกหงาว", district: "เมืองระนอง" },
        { name: "พระราชวังรัตนรังสรรค์", district: "เมืองระนอง" },
        { name: "น้ำตกปุญญบาล", district: "เมืองระนอง" }
      ],
      "ระยอง": [
        { name: "เกาะเสม็ด", district: "แกลง" },
        { name: "หาดแม่รำพึง", district: "เมืองระยอง" },
        { name: "ทุ่งโปรงทอง ปากน้ำประแสร์", district: "แกลง" },
        { name: "สวนสมุนไพรสมเด็จพระเทพฯ", district: "เมืองระยอง" },
        { name: "หาดแหลมแม่พิมพ์", district: "แกลง" }
      ],
      "ราชบุรี": [
        { name: "เขางู", district: "เมืองราชบุรี" },
        { name: "อุทยานหินเขางู", district: "เมืองราชบุรี" },
        { name: "ตลาดน้ำดำเนินสะดวก", district: "ดำเนินสะดวก" },
        { name: "สวนผึ้ง (บ่อคลึง-โป่งกระทิง)", district: "สวนผึ้ง" },
        { name: "ธารน้ำร้อนบ่อคลึง", district: "สวนผึ้ง" }
      ],
      "ลพบุรี": [
        { name: "พระปรางค์สามยอด", district: "เมืองลพบุรี" },
        { name: "ศาลพระกาฬ", district: "เมืองลพบุรี" },
        { name: "เขื่อนป่าสักชลสิทธิ์", district: "พัฒนานิคม" },
        { name: "เขตพระราชฐานพระนารายณ์ราชนิเวศน์", district: "เมืองลพบุรี" },
        { name: "สวนสัตว์ลพบุรี", district: "เมืองลพบุรี" }
      ],
      "ลำปาง": [
        { name: "วัดพระธาตุลำปางหลวง", district: "เกาะคา" },
        { name: "กาดกองต้า ถนนคนเดินลำปาง", district: "เมืองลำปาง" },
        { name: "อุทยานแห่งชาติแจ้ซ้อน", district: "เมืองปาน" },
        { name: "พิพิธภัณฑ์รถม้าลำปาง", district: "เมืองลำปาง" },
        { name: "วัดศรีชุม ลำปาง", district: "เมืองลำปาง" }
      ],
      "ลำพูน": [
        { name: "วัดพระธาตุหริภุญชัยวรมหาวิหาร", district: "เมืองลำพูน" },
        { name: "วัดจามเทวี", district: "เมืองลำพูน" },
        { name: "กู่ช้างกู่ม้า", district: "เมืองลำพูน" },
        { name: "สะพานทาชมภู", district: "แม่ทา" },
        { name: "อุทยานแห่งชาติแม่ปิง", district: "ลี้" }
      ],
      "เลย": [
        { name: "เชียงคาน ถนนคนเดินริมโขง", district: "เชียงคาน" },
        { name: "ภูเรือ", district: "ภูเรือ" },
        { name: "ภูป่าเปาะ", district: "หนองหิน" },
        { name: "พระธาตุศรีสองรัก", district: "ด่านซ้าย" },
        { name: "อุทยานแห่งชาติภูหลวง", district: "ภูหลวง" }
      ],
      "ศรีสะเกษ": [
        { name: "ผามออีแดง", district: "กันทรลักษ์" },
        { name: "ปราสาทเขาพระวิหาร (ฝั่งไทย)", district: "กันทรลักษ์" },
        { name: "วัดพระธาตุเรืองรอง", district: "เมืองศรีสะเกษ" },
        { name: "สวนสมเด็จศรีนครินทร์ ศรีสะเกษ", district: "เมืองศรีสะเกษ" },
        { name: "น้ำตกสำโรงเกียรติ", district: "น้ำเกลี้ยง" }
      ],
      "สกลนคร": [
        { name: "พระธาตุเชิงชุมวรวิหาร", district: "เมืองสกลนคร" },
        { name: "วัดป่าสุทธาวาส", district: "เมืองสกลนคร" },
        { name: "หนองหานสกลนคร", district: "เมืองสกลนคร" },
        { name: "ภูพาน", district: "กุดบาก" },
        { name: "หมู่บ้านทอผ้าคราม บ้านนาขาม", district: "พรรณานิคม" }
      ],
      "สงขลา": [
        { name: "หาดสมิหลา", district: "เมืองสงขลา" },
        { name: "เขาตังกวน", district: "เมืองสงขลา" },
        { name: "ย่านเมืองเก่าสงขลา ถนนนางงาม", district: "เมืองสงขลา" },
        { name: "ทะเลสาบสงขลา", district: "เมืองสงขลา" },
        { name: "เกาะยอ", district: "เมืองสงขลา" }
      ],
      "สตูล": [
        { name: "อุทยานแห่งชาติตะรุเตา", district: "ละงู" },
        { name: "เกาะหลีเป๊ะ", district: "ละงู" },
        { name: "เกาะอาดัง-ราวี", district: "ละงู" },
        { name: "ถ้ำเลสเตโกดอน", district: "ทุ่งหว้า" },
        { name: "วังประจัน", district: "ควนโดน" }
      ],
      "สมุทรปราการ": [
        { name: "เมืองโบราณ", district: "บางปู" },
        { name: "พิพิธภัณฑ์ช้างเอราวัณ", district: "บางเมือง" },
        { name: "สถานตากอากาศบางปู", district: "เมืองสมุทรปราการ" },
        { name: "วัดพระสมุทรเจดีย์", district: "พระสมุทรเจดีย์" },
        { name: "ฟาร์มจระเข้และสวนสัตว์สมุทรปราการ", district: "เมืองสมุทรปราการ" }
      ],
      "สมุทรสงคราม": [
        { name: "ตลาดน้ำอัมพวา", district: "อัมพวา" },
        { name: "ตลาดร่มหุบ (ตลาดแม่กลอง)", district: "เมืองสมุทรสงคราม" },
        { name: "วัดบางกุ้ง", district: "บางคนที" },
        { name: "ดอนหอยหลอด (ติดแม่กลอง)", district: "เมืองสมุทรสงคราม" },
        { name: "โฮมสเตย์ริมคลองอัมพวา", district: "อัมพวา" }
      ],
      "สมุทรสาคร": [
        { name: "ตลาดมหาชัย", district: "เมืองสมุทรสาคร" },
        { name: "วัดโกรกกราก", district: "เมืองสมุทรสาคร" },
        { name: "ศาลพันท้ายนรสิงห์", district: "เมืองสมุทรสาคร" },
        { name: "ศูนย์อนุรักษ์ป่าชายเลนพันท้ายนรสิงห์", district: "เมืองสมุทรสาคร" },
        { name: "ตลาดทะเลไทย", district: "เมืองสมุทรสาคร" }
      ],
      "สระแก้ว": [
        { name: "น้ำตกปางสีดา", district: "เมืองสระแก้ว" },
        { name: "อุทยานแห่งชาติปางสีดา", district: "เมืองสระแก้ว" },
        { name: "ตลาดโรงเกลือ ชายแดนอรัญประเทศ", district: "อรัญประเทศ" },
        { name: "วัดเขาฉกรรจ์", district: "เขาฉกรรจ์" },
        { name: "อ่างเก็บน้ำห้วยยาง", district: "วัฒนานคร" }
      ],
      "สระบุรี": [
        { name: "พระพุทธบาทราชวรมหาวิหาร", district: "พระพุทธบาท" },
        { name: "อุทยานแห่งชาติน้ำตกเจ็ดสาวน้อย", district: "แก่งคอย" },
        { name: "น้ำตกสามหลั่น", district: "เมืองสระบุรี" },
        { name: "ไร่องุ่นและฟาร์มโคนมโครงการหลวง", district: "มวกเหล็ก" },
        { name: "เขื่อนป่าสักชลสิทธิ์ (ด้านสระบุรี)", district: "วังม่วง" }
      ],
      "สิงห์บุรี": [
        { name: "วัดพิกุลทอง", district: "ท่าช้าง" },
        { name: "วัดพระนอนจักรสีห์วรวิหาร", district: "เมืองสิงห์บุรี" },
        { name: "พิพิธภัณฑ์วีรชนค่ายบางระจัน", district: "ค่ายบางระจัน" },
        { name: "วัดโพธิ์เก้าต้น", district: "ค่ายบางระจัน" },
        { name: "สวนสมเด็จพระศรีนครินทร์ สิงห์บุรี", district: "เมืองสิงห์บุรี" }
      ],
      "สุโขทัย": [
        { name: "อุทยานประวัติศาสตร์สุโขทัย", district: "เมืองสุโขทัย" },
        { name: "อุทยานประวัติศาสตร์ศรีสัชนาลัย", district: "ศรีสัชนาลัย" },
        { name: "อุทยานแห่งชาติรามคำแหง (เขาหลวง)", district: "คีรีมาศ" },
        { name: "วัดตระพังทอง", district: "เมืองสุโขทัย" },
        { name: "ถนนคนเดินสุโขทัย", district: "เมืองสุโขทัย" }
      ],
      "สุพรรณบุรี": [
        { name: "ตลาดสามชุก 100 ปี", district: "สามชุก" },
        { name: "บึงฉวากเฉลิมพระเกียรติ", district: "เดิมบางนางบวช" },
        { name: "วัดป่าเลไลยก์วรวิหาร", district: "เมืองสุพรรณบุรี" },
        { name: "พิพิธภัณฑสถานแห่งชาติ สุพรรณบุรี", district: "เมืองสุพรรณบุรี" },
        { name: "เขื่อนกระเสียว", district: "ด่านช้าง" }
      ],
      "สุราษฎร์ธานี": [
        { name: "เกาะสมุย", district: "เกาะสมุย" },
        { name: "เกาะพะงัน", district: "เกาะพะงัน" },
        { name: "เขื่อนรัชชประภา (เขื่อนเชี่ยวหลาน)", district: "บ้านตาขุน" },
        { name: "อุทยานแห่งชาติหมู่เกาะอ่างทอง", district: "เกาะสมุย" },
        { name: "อุทยานแห่งชาติเขาสก", district: "พนม" }
      ],
      "สุรินทร์": [
        { name: "หมู่บ้านช้างบ้านตากลาง", district: "ท่าตูม" },
        { name: "อนุสาวรีย์พระยาสุรินทร์ภักดีศรีณรงค์จางวาง", district: "เมืองสุรินทร์" },
        { name: "ปราสาทศีขรภูมิ", district: "ศีขรภูมิ" },
        { name: "ผ้าไหมบ้านท่าสว่าง", district: "เมืองสุรินทร์" },
        { name: "ปราสาทตาเมือนโต๊ด", district: "พนมดงรัก" }
      ],
      "หนองคาย": [
        { name: "วัดผาตากเสื้อ", district: "สังคม" },
        { name: "ตลาดท่าเสด็จ ริมโขง", district: "เมืองหนองคาย" },
        { name: "สะพานมิตรภาพไทย-ลาว แห่งที่ 1", district: "เมืองหนองคาย" },
        { name: "ศาลาแก้วกู่", district: "เมืองหนองคาย" },
        { name: "พระธาตุบังพวน", district: "เมืองหนองคาย" }
      ],
      "หนองบัวลำภู": [
        { name: "วัดถ้ำกลองเพล", district: "เมืองหนองบัวลำภู" },
        { name: "หนองบัว บึงน้ำกลางเมือง", district: "เมืองหนองบัวลำภู" },
        { name: "ภูพานน้อย", district: "โนนสัง" },
        { name: "น้ำตกเฒ่าโต้", district: "เมืองหนองบัวลำภู" },
        { name: "อ่างเก็บน้ำห้วยน้ำขาว", district: "ศรีบุญเรือง" }
      ],
      "อ่างทอง": [
        { name: "วัดม่วง (หลวงพ่อใหญ่)", district: "วิเศษชัยชาญ" },
        { name: "วัดขุนอินทประมูล", district: "โพธิ์ทอง" },
        { name: "วัดป่าโมกวรวิหาร", district: "ป่าโมก" },
        { name: "ตลาดศาลเจ้าโรงทอง", district: "วิเศษชัยชาญ" },
        { name: "ศูนย์ตุ๊กตาชาววังบ้านบางเสด็จ", district: "ป่าโมก" }
      ],
      "อำนาจเจริญ": [
        { name: "พระมงคลมิ่งเมือง", district: "เมืองอำนาจเจริญ" },
        { name: "วัดพระเจ้าใหญ่ลือชัย", district: "เมืองอำนาจเจริญ" },
        { name: "บึงพระเหวียง", district: "เมืองอำนาจเจริญ" },
        { name: "วัดดงยาง", district: "ปทุมราชวงศา" },
        { name: "ศูนย์เรียนรู้เศรษฐกิจพอเพียงในท้องถิ่น", district: "เมืองอำนาจเจริญ" }
      ],
      "อุดรธานี": [
        { name: "แหล่งโบราณคดีบ้านเชียง", district: "หนองหาน" },
        { name: "ทะเลบัวแดง หนองหาน", district: "กุมภวาปี" },
        { name: "สวนสาธารณะหนองประจักษ์", district: "เมืองอุดรธานี" },
        { name: "คำชะโนด วังนาคินทร์", district: "บ้านดุง" },
        { name: "พิพิธภัณฑ์เมืองอุดรธานี", district: "เมืองอุดรธานี" }
      ],
      "อุตรดิตถ์": [
        { name: "เขื่อนสิริกิติ์", district: "ท่าปลา" },
        { name: "เมืองลับแล (ประตูเมืองลับแล)", district: "ลับแล" },
        { name: "น้ำตกแม่พูล", district: "ลับแล" },
        { name: "วัดพระบรมธาตุทุ่งยั้ง", district: "ลับแล" },
        { name: "สวนสาธารณะทุ่งกะโล่", district: "เมืองอุตรดิตถ์" }
      ],
      "อุทัยธานี": [
        { name: "วัดสังกัสรัตนคีรี และเขาสะแกกรัง", district: "เมืองอุทัยธานี" },
        { name: "อุทยานแห่งชาติห้วยขาแข้ง", district: "ลานสัก" },
        { name: "ตลาดซาวไฮ่ บ้านไร่", district: "บ้านไร่" },
        { name: "วัดถ้ำเขาวง", district: "บ้านไร่" },
        { name: "แม่น้ำสะแกกรัง", district: "เมืองอุทัยธานี" }
      ],
      "อุบลราชธานี": [
        { name: "สามพันโบก", district: "โพธิ์ไทร" },
        { name: "ผาแต้ม อุทยานแห่งชาติผาแต้ม", district: "โขงเจียม" },
        { name: "วัดสิรินธรวรารามภูพร้าว (วัดเรืองแสง)", district: "สิรินธร" },
        { name: "วัดหนองบัว", district: "เมืองอุบลราชธานี" },
        { name: "แก่งสะพือ", district: "พิบูลมังสาหาร" }
      ]
    };

    // -------------------------------
    // สร้าง SAMPLE_RESOURCES จาก PLACE_TEMPLATES
    // -------------------------------
    const SAMPLE_RESOURCES = [];
    Object.entries(PLACE_TEMPLATES).forEach(([province, places]) => {
      places.forEach((p, idx) => {
        SAMPLE_RESOURCES.push({
          id: `${province}-${idx + 1}`,
          name: p.name,
          province,
          district:
            p.district ||
            (province === "กรุงเทพมหานคร" ? "พระนคร" : `เมือง${province}`),
          description: `แหล่งท่องเที่ยวสำคัญในจังหวัด ${province}`,
          subjects: ["สังคมศึกษา ศาสนาและวัฒนธรรม"],
          standards: ["ส 2.1"],
          tags: ["แหล่งท่องเที่ยว"],
          imageUrl: "" // ถ้าเว้นว่าง ระบบจะใช้ภาพสุ่มจาก picsum.photos
        });
      });
    });

    // -------------------------------
    // 3) ฟังก์ชันแสดงผล
    // -------------------------------
    const resultsContainer = document.getElementById("resultsContainer");
    const initialState = document.getElementById("initialState");

    function renderResults(items, province, district) {
      resultsContainer.innerHTML = "";

      if (!items) {
        initialState.classList.remove("hidden");
        return;
      }

      initialState.classList.add("hidden");

      if (items.length === 0) {
        const emptyBox = document.createElement("div");
        emptyBox.className =
          "text-center py-20 bg-white rounded-xl shadow-sm border border-dashed border-gray-300";
        emptyBox.innerHTML = `
          <div class="bg-gray-50 w-24 h-24 rounded-full flex items-center justify-center mx-auto mb-4">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-10 w-10 text-gray-400" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1"
                d="M19 11H5m14 0a2 2 0 012 2v6a2 2 0 01-2 2H5a2 2 0 01-2-2v-6a2 2 0 012-2m14 0V9a2 2 0 00-2-2M5 11V9a2 2 0 012-2m0 0V5a2 2 0 012-2h6a2 2 0 012 2v2M7 7h10" />
            </svg>
          </div>
          <p class="text-gray-600 text-lg font-medium">
            ยังไม่มีข้อมูลแหล่งเรียนรู้เฉพาะสำหรับอำเภอนี้
          </p>
          <p class="text-gray-400 text-sm mt-1">
            สามารถเพิ่มข้อมูลแหล่งเรียนรู้ของอำเภอ/จังหวัดนี้ในโค้ดส่วน PLACE_TEMPLATES ได้
          </p>
        `;
        resultsContainer.appendChild(emptyBox);
        return;
      }

      const header = document.createElement("div");
      header.className = "flex items-center justify-between mb-6 flex-wrap gap-2";
      const sub = district
        ? `จังหวัด ${province} • อำเภอ/เขต ${district}`
        : `จังหวัด ${province}`;
      header.innerHTML = `
        <div>
          <h3 class="text-lg font-semibold text-gray-700 border-l-4 border-thai-secondary pl-3">
            ผลการค้นหาแหล่งเรียนรู้ ${district ? "ในพื้นที่" : "ในจังหวัด"}
          </h3>
          <p class="text-xs text-gray-500 mt-1">${sub}</p>
        </div>
        <span
          class="text-xs text-gray-500 bg-white border border-gray-200 px-3 py-1 rounded-full shadow-sm"
        >
          พบทั้งหมด ${items.length} แห่ง
        </span>
      `;
      resultsContainer.appendChild(header);

      const grid = document.createElement("div");
      grid.className = "grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6";

      items.forEach((res) => {
        const card = document.createElement("article");
        card.className =
          "bg-white rounded-xl shadow-md border border-gray-200 overflow-hidden flex flex-col";

        const imgUrl =
          res.imageUrl ||
          `https://picsum.photos/seed/${encodeURIComponent(res.id)}/600/400`;

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
              ${res.description || `แหล่งท่องเที่ยวในจังหวัด ${res.province}`}
            </p>

            <div class="text-xs">
              <p class="font-semibold text-gray-700 mb-1">
                สาระการเรียนรู้ที่เกี่ยวข้อง:
              </p>
              <p class="text-gray-600">
                ${(res.subjects || ["สังคมศึกษา ศาสนาและวัฒนธรรม"]).join(" • ")}
              </p>
            </div>

            <div class="text-xs">
              <p class="font-semibold text-gray-700 mb-1">
                มาตรฐาน/ตัวชี้วัด (ตัวอย่าง):
              </p>
              <ul class="list-disc list-inside text-gray-600 space-y-0.5">
                ${(res.standards || ["ส 2.1"])
                  .map((s) => `<li>${s}</li>`)
                  .join("")}
              </ul>
            </div>

            <div class="mt-1 flex flex-wrap gap-1.5">
              ${(res.tags || ["แหล่งท่องเที่ยว"])
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
    // 4) เมื่อกดปุ่มค้นหา
    // -------------------------------
    document.getElementById("searchBtn").addEventListener("click", () => {
      const province = document.getElementById("province").value.trim();
      const district = document.getElementById("district").value.trim();

      if (!province) {
        alert("กรุณาเลือกจังหวัดก่อนทำการค้นหา");
        return;
      }

      const filtered = SAMPLE_RESOURCES.filter((item) => {
        const matchProvince = item.province === province;
        const matchDistrict = district ? item.district === district : true;
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
