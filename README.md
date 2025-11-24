<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title id="pageTitle">أكاديمية الزرقاء - الهيكل التنظيمي الرسمي 2025</title>
    <script src="https://cdn.jsdelivr.net/npm/sweetalert2@11"></script>
    <script src="https://cdn.jsdelivr.net/npm/org-chart@2.0.6/dist/js/orgchart.min.js"></script>
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/org-chart@2.0.6/dist/css/orgchart.min.css">
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Cairo:wght@400;600;700;900&display=swap');
        *{box-sizing:border-box;margin:0;padding:0;}
        body{font-family:'Cairo',sans-serif;background:#f5f9ff;color:#2d3748;}
        .container{max-width:1920px;margin:20px auto;background:white;border-radius:32px;box-shadow:0 40px 120px rgba(0,75,138,0.25);overflow:hidden;}
        header{background:linear-gradient(135deg,#003c70,#005a9e);color:white;text-align:center;padding:70px 20px;}
        h1#mainTitle{font-size:56px;font-weight:900;margin:0;cursor:pointer;}
        .subtitle#mainSubtitle{font-size:30px;margin-top:16px;opacity:0.94;cursor:pointer;}

        .tabs{display:flex;background:#003c70;color:white;}
        .tab{flex:1;padding:26px;text-align:center;font-size:24px;cursor:pointer;transition:0.4s;font-weight:700;}
        .tab.active,.tab:hover{background:#005a9e;color:#00ffff;}

        .tab-content{display:none;padding:60px 40px;background:#f9fcff;min-height:1000px;}
        .tab-content.active{display:block;}

        /* الخط + الزر الأزرق المتوهج تمامًا مثل الصورة */
        .divider-line{
            position:relative;height:6px;
            background:linear-gradient(to right, transparent 5%, #00d4ff 30%, #0099cc 50%, #00d4ff 70%, transparent 95%);
            margin:140px auto 100px;width:94%;max-width:1800px;border-radius:10px;
            filter:drop-shadow(0 0 20px rgba(0,212,255,0.7));
        }
        .add-on-line{
            position:absolute;top:50%;left:50%;transform:translate(-50%,-50%);
            width:90px;height:90px;background:#00d4ff;color:#003c70;border-radius:50%;
            font-size:50px;font-weight:900;border:none;cursor:pointer;
            display:flex;align-items:center;justify-content:center;
            box-shadow:0 0 40px rgba(0,212,255,0.8),0 0 80px rgba(0,212,255,0.4);
            transition:all 0.4s;z-index:100;
        }
        .add-on-line:hover{transform:translate(-50%,-50%) scale(1.2);background:#00eeff;
            box-shadow:0 0 60px rgba(0,212,255,1),0 0 120px rgba(0,212,255,0.6);}

        .branches{display:flex;justify-content:center;flex-wrap:wrap;gap:110px;margin-top:60px;}
        .central-group,.branch-group{position:relative;padding:50px;border-radius:36px;background:rgba(44,122,210,0.08);
            box-shadow:0 20px 60px rgba(0,0,0,0.15);transition:0.5s;}
        .central-group:hover,.branch-group:hover{transform:translateY(-12px);box-shadow:0 30px 80px rgba(0,0,0,0.22);}

        .box,.subdept,.local{background:white;border-radius:28px;padding:40px 50px;
            box-shadow:0 20px 60px rgba(0,0,0,0.2);min-width:380px;position:relative;}
        .ceo{background:#003c70;color:white;font-size:34px;font-weight:900;padding:50px;}
        .ceo .name{color:white;font-size:30px;margin-top:18px;}
        .central{border:7px solid #0b4b8a;background:#e8f4ff;color:#003c70;font-size:24px 'Cairo';}
        .branch{background:#2c7ad2;color:white;font-size:26px;font-weight:bold;}
        .name{margin-top:20px;padding-top:18px;border-top:4px solid #ddd;font-size:24px;font-weight:bold;color:#003c70;}

        .del-small,.add-small{
            position:absolute;top:15px;width:44px;height:44px;border-radius:50%;border:none;cursor:pointer;
            font-size:24px;box-shadow:0 8px 25px rgba(0,0,0,0.35);opacity:0;transition:0.4s;z-index:10;}
        .del-small{right:15px;background:#e74c3c;color:white;}
        .add-small{left:15px;background:#27ae60;color:white;}
        .central-group:hover .del-small,.central-group:hover .add-small,
        .branch-group:hover .del-small,.branch-group:hover .add-small,
        .subdept:hover .del-small,.subdept:hover .add-small,
        .local:hover .del-small{opacity:0.95;transform:scale(1.1);}

        .connector{height:110px;width:6px;background:#0b4b8a;margin:0 auto;border-radius:3px;}
        footer{background:#003c70;color:white;text-align:center;padding:50px;font-size:20px;}
        #treeView{height:1200px;background:white;border-radius:24px;overflow:auto;padding:40px;}
    </style>
</head>
<body>

<div class="container">
    <header>
        <h1 id="mainTitle" class="editable">أكاديمية الزرقاء</h1>
        <div id="mainSubtitle" class="subtitle editable">الهيكل التنظيمي الرسمي 2025</div>
    </header>

    <div class="tabs">
        <div class="tab active" onclick="openTab('edit')">تحرير الهيكل</div>
        <div class="tab" onclick="openTab('tree')">العرض الشجري</div>
    </div>

    <div id="edit" class="tab-content active">
        <div style="text-align:center;margin:80px 0;">
            <div class="box ceo">الشركة القابضة<br><span id="companyNameSpan">أكاديمية الزرقاء</span></div>
            <div class="connector"></div>
            <div class="box ceo editable">الرئيس التنفيذي
                <div class="name editable">د. أحمد بن عبدالله الزرقاء</div>
            </div>
        </div>

        <!-- زر إضافة قسم مركزي -->
        <div class="divider-line"><button class="add-on-line" onclick="addCentralPrompt()">+</button></div>

        <!-- الأقسام المركزية (مملوءة افتراضيًا) -->
        <div class="branches" id="centralDepts">
            <div class="central-group">
                <button class="add-small" onclick="addCentralPrompt()">+</button>
                <button class="del-small" onclick="confirmDelete(this.parentElement)">X</button>
                <div class="box central editable">الإدارة المركزية<br>(تسويق، مبيعات، موارد بشرية، IT، خدمة عملاء)</div>
                <div class="name editable">أ. محمد بن عبدالله العتيبي</div>
            </div>
            <div class="central-group">
                <button class="add-small" onclick="addCentralPrompt()">+</button>
                <button class="del-small" onclick="confirmDelete(this.parentElement)">X</button>
                <div class="box central editable">الإدارة المالية والمحاسبة</div>
                <div class="name editable">أ. سارة بنت عبدالرحمن الدوسري</div>
            </div>
            <div class="central-group">
                <button class="add-small" onclick="addCentralPrompt()">+</button>
                <button class="del-small" onclick="confirmDelete(this.parentElement)">X</button>
                <div class="box central editable">إدارة العمليات والجودة</div>
                <div class="name editable">أ. لينا بنت خالد الفهد</div>
            </div>
        </div>

        <!-- زر إضافة فرع جديد -->
        <div class="divider-line"><button class="add-on-line" onclick="addNewBranch()">+</button></div>

        <!-- الفروع (مملوءة افتراضيًا بالكامل) -->
        <div class="branches" id="branches">
            <div class="branch-group">
                <button class="add-small" onclick="addSubPrompt(this)">+</button>
                <button class="del-small" onclick="confirmDelete(this.parentElement)">X</button>
                <div class="box branch editable">أكاديمية الزرقاء - الرياض</div>
                <div class="name editable">أ. خالد بن عبدالله الشمري</div>
                <div class="subdepts-container">
                    <div class="subdept">
                        <button class="add-small" onclick="addPosPrompt(this)">+</button>
                        <button class="del-small" onclick="confirmDelete(this.parentElement)">X</button>
                        <strong class="editable">قسم التدريب الميداني</strong><br>
                        <div class="name editable">ريم بنت فهد الدخيل</div>
                        <div class="local editable">منسق برامج<br><span class="name editable">سعود الدخيل</span>
                            <button class="del-small" onclick="confirmDelete(this.parentElement)">X</button>
                        </div>
                    </div>
                </div>
            </div>

            <div class="branch-group">
                <button class="add-small" onclick="addSubPrompt(this)">+</button>
                <button class="del-small" onclick="confirmDelete(this.parentElement)">X</button>
                <div class="box branch editable">أكاديمية الزرقاء - جدة</div>
                <div class="name editable">أ. فاطمة بنت علي البقمي</div>
                <div class="subdepts-container">
                    <div class="subdept">
                        <button class="add-small" onclick="addPosPrompt(this)">+</button>
                        <button class="del-small" onclick="confirmDelete(this.parentElement)">X</button>
                        <strong class="editable">قسم التدريب</strong><br>
                        <div class="name editable">سارة بنت أحمد الغامدي</div>
                    </div>
                </div>
            </div>

            <div class="branch-group">
                <button class="add-small" onclick="addSubPrompt(this)">+</button>
                <button class="del-small" onclick="confirmDelete(this.parentElement)">X</button>
                <div class="box branch editable">أكاديمية الزرقاء - أونلاين</div>
                <div class="name editable">أ. مشاري بن عبدالله الراجحي</div>
                <div class="subdepts-container">
                    <div class="subdept">
                        <button class="add-small" onclick="addPosPrompt(this)">+</button>
                        <button class="del-small" onclick="confirmDelete(this.parentElement)">X</button>
                        <strong class="editable">قسم المنصة الإلكترونية</strong><br>
                        <div class="name editable">يوسف التميمي</div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <div id="tree" class="tab-content">
        <div style="text-align:center;padding:40px;">
            <h2 style="color:#003c70;font-size:36px;">العرض الشجري التفاعلي</h2>
            <button style="padding:18px 70px;background:#003c70;color:white;border:none;border-radius:50px;font-size:24px;cursor:pointer;" onclick="renderTree()">تحديث العرض الشجري</button>
        </div>
        <div id="treeView"></div>
    </div>

    <footer id="footerText">أكاديمية الزرقاء © 2025 – الإصدار الرسمي المُعتمد</footer>
</div>

<script>
function updateAllNames() {
    const name = document.getElementById("mainTitle").innerText.trim();
    const year = document.getElementById("mainSubtitle").innerText.match(/\d{4}/)?.[0] || new Date().getFullYear();
    document.getElementById("pageTitle").innerText = `${name} - الهيكل التنظيمي الرسمي ${year}`;
    document.getElementById("companyNameSpan").innerText = name;
    document.getElementById("footerText").innerHTML = `${name} © ${year} – الإصدار الرسمي المُعتمد`;
    document.querySelectorAll(".box.branch").forEach(el => {
        const parts = el.innerText.split(" - ");
        if(parts.length > 1) el.innerText = `${name} - ${parts[1]}`;
    });
}

function openTab(t){
    document.querySelectorAll('.tab-content').forEach(x=>x.classList.remove('active'));
    document.querySelectorAll('.tab').forEach(x=>x.classList.remove('active'));
    document.getElementById(t).classList.add('active');
    document.querySelector(`.tab[onclick="openTab('${t}')"]`).classList.add('active');
    if(t==='tree') renderTree();
}

function save(){
    localStorage.setItem('alzarkaa_2025_final_full', JSON.stringify({
        edit: document.getElementById('edit').innerHTML,
        title: document.getElementById('mainTitle').innerText,
        subtitle: document.getElementById('mainSubtitle').innerText
    }));
}

function load(){
    const saved = localStorage.getItem('alzarkaa_2025_final_full');
    if(saved){
        const d = JSON.parse(saved);
        document.getElementById('edit').innerHTML = d.edit;
        document.getElementById('mainTitle').innerText = d.title;
        document.getElementById('mainSubtitle').innerText = d.subtitle;
    }
    updateAllNames();
    renderTree();
}

function confirmDelete(el){
    const name = el.querySelector('.box, strong, .local')?.innerText || "العنصر";
    Swal.fire({title:'تأكيد الحذف',text:`هل تريد حذف ${name}؟`,icon:'warning',showCancelButton:true,
        confirmButtonText:'نعم',cancelButtonText:'إلغاء'})
    .then(r=>{if(r.isConfirmed){el.remove();save();renderTree();}});
}

document.addEventListener('click', e=>{
    const el = e.target.closest('.editable');
    if(el){
        el.contentEditable = true; el.focus();
        el.style.outline = '5px solid #00d4ff'; el.style.borderRadius = '16px';
        el.onblur = () => {
            el.contentEditable = false; el.style.outline = '';
            if(el.id==='mainTitle' || el.id==='mainSubtitle') updateAllNames();
            save(); renderTree();
        };
        el.onkeydown = ev => {if(ev.key==='Enter'){ev.preventDefault();el.blur();}}
    }
});

function addCentralPrompt(){
    Swal.fire({title:'قسم مركزي جديد',html:'<input id="t" class="swal2-input" placeholder="اسم القسم"><input id="m" class="swal2-input" placeholder="المدير">',showCancelButton:true})
    .then(r=>{if(r.isConfirmed){
        const t = document.getElementById('t').value || 'قسم جديد';
        const m = document.getElementById('m').value || '— مدير —';
        const div = document.createElement('div'); div.className='central-group';
        div.innerHTML = `<button class="add-small" onclick="addCentralPrompt()">+</button><button class="del-small" onclick="confirmDelete(this.parentElement)">X</button>
            <div class="box central editable">${t}</div><div class="name editable">${m}</div>`;
        document.getElementById('centralDepts').appendChild(div);
        save(); renderTree();
    }});
}

function addNewBranch(){
    Swal.fire({title:'فرع جديد',html:'<input id="c" class="swal2-input" placeholder="المدينة"><input id="m" class="swal2-input" placeholder="مدير الفرع">',showCancelButton:true})
    .then(r=>{if(r.isConfirmed){
        const city = document.getElementById('c').value || 'فرع جديد';
        const manager = document.getElementById('m').value || '— مدير —';
        const div = document.createElement('div'); div.className='branch-group';
        div.innerHTML = `<button class="add-small" onclick="addSubPrompt(this)">+</button><button class="del-small" onclick="confirmDelete(this.parentElement)">X</button>
            <div class="box branch editable">${document.getElementById('mainTitle').innerText} - ${city}</div>
            <div class="name editable">${manager}</div><div class="subdepts-container"></div>`;
        document.getElementById('branches').appendChild(div);
        save(); renderTree();
    }});
}

function addSubPrompt(btn){
    Swal.fire({title:'قسم فرعي جديد',html:'<input id="n" class="swal2-input" placeholder="اسم القسم"><input id="m" class="swal2-input" placeholder="المدير">',showCancelButton:true})
    .then(r=>{if(r.isConfirmed){
        const s = document.createElement('div'); s.className='subdept';
        s.innerHTML = `<button class="add-small" onclick="addPosPrompt(this)">+</button><button class="del-small" onclick="confirmDelete(this.parentElement)">X</button>
            <strong class="editable">${document.getElementById('n').value||'قسم جديد'}</strong><br><div class="name editable">${document.getElementById('m').value||'— مدير —'}</div>`;
        btn.parentElement.querySelector('.subdepts-container').appendChild(s);
        save(); renderTree();
    }});
}

function addPosPrompt(btn){
    Swal.fire({title:'منصب جديد',input:'text',inputPlaceholder:'المسمى – الاسم',showCancelButton:true})
    .then(r=>{if(r.value){
        const [job, name='—'] = r.value.split(' – ');
        const e = document.createElement('div'); e.className='local editable';
        e.innerHTML = `${job}<br><span class="name editable">${name.trim()}</span><button class="del-small" onclick="confirmDelete(this.parentElement)">X</button>`;
        btn.parentElement.appendChild(e);
        save(); renderTree();
    }});
}

function renderTree(){
    const name = document.getElementById("mainTitle").innerText.trim();
    const data = {name, title:"الشركة القابضة", className:"ceo",
        children:[{
            name:document.querySelector('.ceo .name')?.innerText.trim()||"الرئيس التنفيذي",
            title:"الرئيس التنفيذي", className:"ceo",
            children:[
                ...Array.from(document.querySelectorAll('#centralDepts .central-group')).map(g=>({
                    name:g.querySelector('.central')?.innerHTML.replace(/<br>/g,' ')||"قسم",
                    title:g.querySelector('.name')?.innerText||"", className:"central"
                })),
                ...Array.from(document.querySelectorAll('#branches .branch-group')).map(b=>({
                    name:b.querySelector('.branch')?.innerText||"فرع",
                    title:b.querySelector('.name')?.innerText||"", className:"branch",
                    children:Array.from(b.querySelectorAll('.subdept')).map(s=>({
                        name:s.querySelector('strong')?.innerText||"قسم فرعي",
                        title:s.querySelector('.name')?.innerText||"", className:"subdept",
                        children:Array.from(s.querySelectorAll('.local')).map(l=>({
                            name:l.childNodes[0]?.nodeValue?.trim()||"منصب",
                            title:l.querySelector('.name')?.innerText||"", className:"local"
                        }))
                    }))
                }))
            ]
        }]
    };
    document.getElementById('treeView').innerHTML = '';
    new OrgChart(document.getElementById('treeView'), {pan:true,zoom:true,direction:'t2b',
        nodeBinding:{field_0:"name",field_1:"title"},
        nodeTemplate:d=>`<div class="title">${d.name}</div><div class="content">${d.title}</div>`
    }).loadData(data);
}

window.onload = load;
</script>
</body>
</html>
