<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>أكاديمية الزرقاء - الهيكل التنظيمي الرسمي 2025</title>
    <meta name="description" content="الهيكل التنظيمي التفاعلي لأكاديمية الزرقاء - 2025">
    <script src="https://cdn.jsdelivr.net/npm/sweetalert2@11"></script>
    <script src="https://cdn.jsdelivr.net/npm/org-chart@2.0.6/dist/js/orgchart.min.js"></script>
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/org-chart@2.0.6/dist/css/orgchart.min.css">
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Cairo:wght@400;600;700;900&display=swap');
        *{box-sizing:border-box;margin:0;padding:0;}
        body{font-family:'Cairo',sans-serif;background:linear-gradient(135deg,#f0f4f8,#d9e2ec);color:#2d3748;}
        .container{max-width:1920px;margin:20px auto;background:white;border-radius:20px;box-shadow:0 30px 100px rgba(0,75,138,0.25);overflow:hidden;}
        header{background:linear-gradient(90deg,#003c70,#0b4b8a);color:white;text-align:center;padding:50px 20px;}
        h1{margin:0;font-size:48px;font-weight:900;}
        .subtitle{font-size:26px;margin-top:12px;opacity:0.95;}
        .tabs{display:flex;background:#003c70;color:white;}
        .tab{flex:1;padding:22px;text-align:center;font-size:22px;cursor:pointer;transition:0.3s;}
        .tab.active,.tab:hover{background:#0b4b8a;font-weight:bold;}
        .tab-content{display:none;padding:40px;background:#f9fcff;min-height:800px;}
        .tab-content.active{display:block;}
        #treeView{height:1000px;background:white;border-radius:16px;overflow:auto;position:relative;}
        .orgchart .node{text-align:center !important;padding:20px !important;border-radius:20px !important;box-shadow:0 10px 30px rgba(0,0,0,0.2) !important;}
        .orgchart .title{font-weight:900;font-size:19px;line-height:1.4;}
        .orgchart .content{font-size:17px;margin-top:8px;font-weight:600;}
        .node.ceo{background:#003c70 !important;color:white !important;}
        .node.ceo .title,.node.ceo .content{color:white !important;}
        .node.central{background:#e8f4ff !important;border:5px solid #0b4b8a !important;color:#003c70 !important;}
        .node.branch{background:#2c7ad2 !important;color:white !important;}
        .node.subdept{background:#f0f8ff !important;border:3px solid #2c7ad2 !important;color:#003c70 !important;}
        .node.local{background:#f8fbff !important;border:2px dashed #90b8e0 !important;color:#003c70 !important;font-size:15px !important;}
        .big-btn{display:block;margin:50px auto;padding:20px 80px;background:#003c70;color:white;border:none;border-radius:50px;font-size:24px;cursor:pointer;box-shadow:0 12px 30px rgba(0,0,0,0.25);transition:0.3s;}
        .big-btn:hover{background:#002850;transform:scale(1.05);}
        footer{background:#003c70;color:white;text-align:center;padding:35px;font-size:18px;}
        .branches{display:flex;justify-content:center;flex-wrap:wrap;gap:70px;margin-top:60px;}
        .branch-group,.central-group{position:relative;padding:35px;border-radius:24px;background:rgba(44,122,210,0.07);box-shadow:0 12px 35px rgba(0,0,0,0.12);text-align:center;min-width:340px;}
        .box,.subdept,.local,.name,strong{text-align:center !important;}
        .box{background:white;border-radius:20px;padding:28px 40px;min-width:320px;box-shadow:0 15px 40px rgba(0,0,0,0.15);}
        .ceo{background:#003c70;color:white;font-size:28px;font-weight:900;}
        .ceo .name{color:white !important;font-size:24px !important;font-weight:900 !important;margin-top:12px;}
        .central{border:5px solid #0b4b8a;background:#e8f4ff;color:#003c70;font-size:20px;}
        .branch{background:#2c7ad2;color:white;font-weight:bold;font-size:22px;}
        .subdept,.local{background:#fff;border-radius:16px;padding:18px;margin:16px 0;box-shadow:0 8px 25px rgba(0,0,0,0.1);}
        .name{margin-top:16px;padding-top:14px;border-top:2px solid #ddd;font-weight:bold;font-size:20px;color:#003c70;}
        .editable{cursor:pointer;transition:0.2s;}
        .editable:hover{background:#e6f7ff;border-radius:12px;padding:8px;}
        .add-btn,.del-btn{position:absolute;top:15px;width:46px;height:46px;border-radius:50%;border:none;cursor:pointer;font-size:26px;color:white;box-shadow:0 6px 18px rgba(0,0,0,0.3);z-index:10;transition:0.3s;}
        .add-btn{left:15px;background:#0b4b8a;}
        .del-btn{right:15px;background:#c53030;}
        .add-btn:hover,.del-btn:hover{transform:scale(1.2);}
        .connector{height:90px;width:4px;background:#0b4b8a;margin:0 auto;}
        .h-connector{height:4px;background:#0b4b8a;width:90%;max-width:1500px;margin:60px auto;}
        @media (max-width:992px){.branches{gap:50px;}.branch-group,.central-group{min-width:300px;}}
        @media (max-width:768px){.branches{flex-direction:column;align-items:center;}.tab{font-size:19px;padding:18px;}}
    </style>
</head>
<body>

<div class="container">
    <header>
        <h1>أكاديمية الزرقاء</h1>
        <div classaeda subtitle">الهيكل التنظيمي الرسمي 2025</div>
    </header>

    <div class="tabs">
        <div class="tab active" onclick="openTab('edit')">تحرير الهيكل</div>
        <div class="tab" onclick="openTab('tree')">العرض الشجري</div>
    </div>

    <div id="edit" class="tab-content active">
        <div id="orgChart"></div>
        <button class="big-btn" onclick="addCentralDept()">إضافة قسم مركزي جديد</button>
        <button class="big-btn" onclick="addNewBranch()">إضافة فرع جديد كامل</button>
    </div>

    <div id="tree" class="tab-content">
        <div style="text-align:center;padding:30px;">
            <h2 style="color:#003c70;">الهيكل التنظيمي - عرض شجري تفاعلي</h2>
            <button class="big-btn" onclick="renderTree()">تحديث العرض الشجري</button>
        </div>
        <div id="treeView"></div>
    </div>

    <footer>أكاديمية الزرقاء © 2025 – هيكل تنظيمي تفاعلي بالكامل • جاهز للنشر على GitHub</footer>
</div>

<script>
function openTab(t){
    document.querySelectorAll('.tab-content').forEach(x=>x.classList.remove('active'));
    document.querySelectorAll('.tab').forEach(x=>x.classList.remove('active'));
    document.getElementById(t).classList.add('active');
    document.querySelector(`.tab[onclick="openTab('${t}')"]`).classList.add('active');
    if(t==='tree') renderTree();
}

function save(){localStorage.setItem('alzarkaa_org_2025', document.getElementById('orgChart').innerHTML);}

document.addEventListener('click', e=>{
    const el = e.target.closest('.editable,.name,strong,.box,.local,.subdept');
    if(!el || el.isContentEditable) return;
    el.contentEditable = true; el.focus();
    el.style.outline = '3px solid #0b4b8a'; el.style.borderRadius = '12px';
    el.onblur = () => {el.contentEditable = false; el.style.outline = ''; save(); renderTree();}
    el.onkeydown = ev => {if(ev.key==='Enter'){ev.preventDefault(); el.blur();}}
});

function load(){
    const saved = localStorage.getItem('alzarkaa_org_2025');
    if(saved){
        document.getElementById('orgChart').innerHTML = saved;
    } else {
        buildFullStructure();
    }
    renderTree();
}

function buildFullStructure(){
    const o = document.getElementById('orgChart');
    o.innerHTML = `
        <div style="text-align:center;margin:50px 0;">
            <div class="box ceo">الشركة القابضة<br>أكاديمية الزرقاء</div>
            <div class="connector"></div>
            <div class="box ceo editable">الرئيس التنفيذي
                <div class="name editable">د. أحمد بن عبدالله الزرقاء</div>
            </div>
        </div>
        <div class="h-connector"></div>
        <div class="branches" id="centralDepts"></div>
        <div class="h-connector"></div>
        <div class="branches" id="branches"></div>`;

    // الأقسام المركزية
    [
        ["الإدارة المركزية<br>(تسويق، مبيعات، موارد بشرية، IT، خدمة عملاء)", "أ. محمد بن عبدالله العتيبي"],
        ["الإدارة المالية والمحاسبة", "أ. سارة بنت عبدالرحمن الدوسري"],
        ["إدارة العمليات والجودة", "أ. لينا بنت خالد الفهد"],
        ["إدارة التطوير والشراكات", "أ. فيصل بن عبدالعزيز الراجحي"]
    ].forEach(d => addCentral(d[0], d[1]));

    // الفروع مع كل التفاصيل
    [
        ["الرياض", "أ. خالد بن عبدالله الشمري", [
            ["قسم التدريب الميداني", "ريم بنت فهد الدخيل", [["منسق برامج تدريبية", "سعود الدخيل"], ["منسق جدولة", "فاطمة الدخيل"]]],
            ["قسم المبيعات والتسويق", "عبدالله بن محمد المهوس", [["مدير مبيعات", "أمل المهوس"], ["مندوب مبيعات", "تركي المهوس"]]],
            ["قسم العمليات والتشغيل", "نورة بنت عبدالرحمن السعيد", [["منسق عمليات", "علي السعيد"]]],
            ["قسم خدمة العملاء", "لطيفة بنت عبدالعزيز العتيبي", [["مشرف خدمة عملاء", "هند العتيبي"]]]
        ]],
        ["جدة", "أ. فاطمة بنت علي البقمي", [
            ["قسم التدريب والتطوير", "سارة بنت أحمد الغامدي", [["منسق تدريب", "خالد الغامدي"]]],
            ["قسم المبيعات", "أحمد بن عبدالله البلوي", [["مدير مبيعات", "نور البلوي"]]]
        ]],
        ["الدمام", "أ. علي بن إبراهيم الدوسري", [
            ["قسم التدريب", "فهد بن عبدالله العنزي", []],
            ["قسم المبيعات", "مريم بنت علي الدوسري", [["مندوبة مبيعات", "سامي الدوسري"]]]
        ]],
        ["أونلاين", "أ. مشاري بن عبدالله الراجحي", [
            ["قسم المنصة الإلكترونية", "يوسف بن عبدالله التميمي", [["مدير تقني", "ليلى التميمي"], ["مطور واجهات", "عبدالله التميمي"]]],
            ["قسم إنتاج المحتوى الرقمي", "نور بنت فهد الزهراني", [["مدير محتوى", "لانا الزهراني"]]],
            ["قسم الدعم الفني", "عبدالرحمن بن خالد الشمري", [["مشرف دعم فني", "هيا الشمري"]]]
        ]]
    ].forEach(b => addFullBranch(b[0], b[1], b[2]));

    save();
}

function addCentral(t,m){
    const d = document.createElement('div'); d.className='central-group';
    d.innerHTML = `<button class="del-btn" onclick="this.parentElement.remove();save();renderTree()">×</button>
        <button class="add-btn" onclick="addPos(this)">+</button>
        <div class="box central editable">${t}</div>
        <div class="name editable">${m}</div>`;
    document.getElementById('centralDepts').appendChild(d);
}

function addFullBranch(city, manager, subdepts){
    const g = document.createElement('div'); g.className='branch-group';
    let subs = '';
    subdepts.forEach(s => {
        let positions = '';
        (s[2] || []).forEach(p => {
            positions += `<div class="local editable">${p[0]}<br><span class="name editable">${p[1]}</span></div>`;
        });
        subs += `<div class="subdept">
            <button class="del-btn" onclick="this.parentElement.remove();save();renderTree()">×</button>
            <button class="add-btn" onclick="addPos(this)">+</button>
            <strong class="editable">${s[0]}</strong><br>
            <div class="name editable">${s[1]}</div>${positions}
        </div>`;
    });
    g.innerHTML = `<button class="del-btn" onclick="this.parentElement.remove();save();renderTree()">×</button>
        <button class="add-btn" onclick="addSub(this)">+</button>
        <div class="box branch editable">أكاديمية الزرقاء - ${city}</div>
        <div class="name editable">${manager}</div>
        <div class="subdepts-container">${subs}</div>
        <button style="margin-top:20px;background:#2c7ad2;color:white;padding:12px 32px;border-radius:40px;border:none;cursor:pointer;" onclick="addSub(this)">⊕ قسم جديد داخل الفرع</button>`;
    document.getElementById('branches').appendChild(g);
}

function addNewBranch(){
    Swal.fire({title:'فرع جديد',html:'<input id="c" class="swal2-input" placeholder="اسم المدينة"><input id="m" class="swal2-input" placeholder="مدير الفرع">',showCancelButton:true,confirmButtonText:'إضافة'}).then(r=>{
        if(r.isConfirmed){
            addFullBranch(document.getElementById('c').value || 'فرع جديد', document.getElementById('m').value || '— مدير الفرع —', []);
            save(); renderTree();
        }
    });
}

function addCentralDept(){
    Swal.fire({title:'قسم مركزي جديد',html:'<input id="t" class="swal2-input" placeholder="اسم القسم"><input id="m" class="swal2-input" placeholder="المدير">',showCancelButton:true}).then(r=>{
        if(r.isConfirmed){
            addCentral(document.getElementById('t').value || 'قسم جديد', document.getElementById('m').value || '— المدير —');
            save(); renderTree();
        }
    });
}

function addSub(btn){
    Swal.fire({title:'قسم جديد في الفرع',html:'<input id="n" class="swal2-input" placeholder="اسم القسم"><input id="m" class="swal2-input" placeholder="مدير القسم">',showCancelButton:true}).then(r=>{
        if(r.isConfirmed){
            const s = document.createElement('div'); s.className='subdept';
            s.innerHTML = `<button class="del-btn" onclick="this.parentElement.remove();save();renderTree()">×</button>
                <button class="add-btn" onclick="addPos(this)">+</button>
                <strong class="editable">${document.getElementById('n').value || 'قسم جديد'}</strong><br>
                <div class="name editable">${document.getElementById('m').value || '— مدير —'}</div>`;
            btn.parentElement.querySelector('.subdepts-container').appendChild(s);
            save(); renderTree();
        }
    });
}

function addPos(btn){
    Swal.fire({title:'منصب جديد',input:'text',inputPlaceholder:'المسمى – الاسم',showCancelButton:true}).then(r=>{
        if(r.value){
            const [job, name = '—'] = r.value.split(' – ');
            const e = document.createElement('div'); e.className='local editable';
            e.innerHTML = `${job}<br><span class="name editable">${name.trim()}</span>`;
            btn.parentElement.appendChild(e);
            save(); renderTree();
        }
    });
}

function renderTree(){
    const data = {
        name: "أكاديمية الزرقاء",
        title: "الشركة القابضة",
        className: "ceo",
        children: [{
            name: document.querySelector('.box.ceo .name')?.innerText.trim() || "د. أحمد الزرقاء",
            title: "الرئيس التنفيذي للمجموعة",
            className: "ceo",
            children: [
                ...Array.from(document.querySelectorAll('#centralDepts .central-group')).map(g => ({
                    name: g.querySelector('.box.central')?.innerHTML.replace(/<br>/g,' ') || "قسم",
                    title: g.querySelector('.name')?.innerText || "",
                    className: "central"
                })),
                ...Array.from(document.querySelectorAll('#branches .branch-group')).map(b => ({
                    name: b.querySelector('.box.branch')?.innerText || "فرع",
                    title: b.querySelector('.name')?.innerText || "",
                    className: "branch",
                    children: Array.from(b.querySelectorAll('.subdept')).map(s => ({
                        name: s.querySelector('strong')?.innerText || "قسم فرعي",
                        title: s.querySelector('.name')?.innerText || "",
                        className: "subdept",
                        children: Array.from(s.querySelectorAll('.local')).map(l => ({
                            name: l.childNodes[0]?.nodeValue?.trim() || "منصب",
                            title: l.querySelector('.name')?.innerText || "",
                            className: "local"
                        }))
                    }))
                }))
            ]
        }]
    };

    document.getElementById('treeView').innerHTML = '';
    new OrgChart(document.getElementById('treeView'), {
        pan: true,
        zoom: true,
        direction: 't2b',
        nodeBinding: { field_0: "name", field_1: "title" },
        nodeTemplate: d => `<div class="title">${d.name}</div><div class="content">${d.title}</div>`
    }).loadData(data);
}

window.onload = load;
</script>
</body>
</html>
