<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>أكاديمية الزرقاء - الهيكل التنظيمي الرسمي 2025</title>
    <script src="https://cdn.jsdelivr.net/npm/sweetalert2@11"></script>
    <script src="https://cdn.jsdelivr.net/npm/org-chart@2.0.6/dist/js/orgchart.min.js"></script>
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/org-chart@2.0.6/dist/css/orgchart.min.css">
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Cairo:wght@400;600;700;900&display=swap');
        body{font-family:'Cairo',sans-serif;background:#f0f4f8;margin:0;color:#2d3748;}
        .container{max-width:1900px;margin:20px auto;background:white;border-radius:20px;box-shadow:0 30px 90px rgba(0,75,138,0.3);overflow:hidden;}
        header{background:linear-gradient(90deg,#003c70,#0b4b8a);color:white;text-align:center;padding:50px 20px;}
        h1{margin:0;font-size:46px;font-weight:900;}
        .tabs{display:flex;background:#003c70;color:white;}
        .tab{flex:1;padding:22px;text-align:center;font-size:22px;cursor:pointer;}
        .tab.active,.tab:hover{background:#0b4b8a;font-weight:bold;}
        .tab-content{display:none;padding:40px;min-height:900px;background:#f9fcff;}
        .tab-content.active{display:block;}
        #treeView{min-height:900px;background:white;border-radius:16px;overflow:auto;padding:20px;box-shadow:inset 0 0 20px rgba(0,0,0,0.05);}
        .orgchart .node{text-align:center !important;padding:18px !important;border-radius:18px !important;font-size:16px !important;box-shadow:0 8px 25px rgba(0,0,0,0.18) !important;}
        .orgchart .node .title{font-weight:900;font-size:18px;margin-bottom:6px;}
        .orgchart .node .content{font-size:16px;margin-top:6px;}
        .node.ceo{background:#003c70 !important;color:white !important;}
        .node.ceo .title,.node.ceo .content{color:white !important;font-weight:900 !important;}
        .node.central{background:#e8f4ff !important;border:4px solid #0b4b8a !important;}
        .node.branch{background:#2c7ad2 !important;color:white !important;}
        .node.subdept{background:#f0f8ff !important;border:3px solid #2c7ad2 !important;}
        .node.local{background:#f8fbff !important;border:2px dashed #90b8e0 !important;font-size:15px !important;}
        .big-btn{display:block;margin:50px auto;padding:20px 80px;background:#003c70;color:white;border:none;border-radius:50px;font-size:24px;cursor:pointer;box-shadow:0 12px 30px rgba(0,0,0,0.25);}
        .big-btn:hover{background:#002850;transform:scale(1.06);}
        footer{background:#003c70;color:white;text-align:center;padding:40px;font-size:19px;}
        .branches{display:flex;justify-content:center;flex-wrap:wrap;gap:70px;margin-top:50px;}
        .branch-group,.central-group{text-align:center;min-width:340px;padding:30px;border-radius:24px;background:rgba(44,122,210,0.08);box-shadow:0 10px 30px rgba(0,0,0,0.12);}
        .box,.subdept,.local,.name,strong,.box *{text-align:center !important;}
        .box{background:white;border-radius:18px;padding:24px 34px;min-width:300px;box-shadow:0 12px 40px rgba(0,0,0,0.15);}
        .ceo{background:#003c70;color:white;font-size:26px;font-weight:900;}
        .ceo .name{color:white !important;font-size:22px !important;font-weight:900 !important;}
        .central{border:5px solid #0b4b8a;background:#e8f4ff;color:#003c70;}
        .branch{background:#2c7ad2;color:white;font-weight:bold;font-size:20px;}
        .subdept,.local{background:#fff;border-radius:14px;padding:16px;margin:14px 0;box-shadow:0 6px 20px rgba(0,0,0,0.1);}
        .name{margin-top:14px;padding-top:12px;border-top:2px solid #ddd;font-weight:bold;font-size:19px;color:#003c70;}
        .editable{cursor:pointer;}
        .editable:hover{background:#e6f7ff;border-radius:10px;padding:6px;}
        .add-btn,.del-btn{position:absolute;top:15px;width:44px;height:44px;border:none;border-radius:50%;cursor:pointer;font-size:24px;color:white;box-shadow:0 6px 16px rgba(0,0,0,0.25);z-index:10;}
        .add-btn{left:15px;background:#0b4b8a;}
        .del-btn{right:15px;background:#c53030;}
        .connector{height:80px;width:4px;background:#0b4b8a;margin:0 auto;}
        .h-connector{height:4px;background:#0b4b8a;width:90%;max-width:1400px;margin:50px auto;}
        @media (max-width:768px){.branches{flex-direction:column;align-items:center;}}
    </style>
</head>
<body>

<div class="container">
    <header>
        <h1>أكاديمية الزرقاء</h1>
        <div style="font-size:26px;margin-top:15px;">الهيكل التنظيمي الرسمي 2025</div>
    </header>

    <div class="tabs">
        <div class="tab active" onclick="openTab('edit')">تحرير الهيكل</div>
        <div class="tab" onclick="openTab('tree')">عرض شجري</div>
    </div>

    <div id="edit" class="tab-content active">
        <div class="org" id="orgChart"></div>
        <button class="big-btn" onclick="addCentralDept()">إضافة قسم مركزي جديد</button>
        <button class="big-btn" onclick="addNewBranch()">إضافة فرع جديد كامل</button>
    </div>

    <div id="tree" class="tab-content">
        <div style="text-align:center;padding:30px;">
            <h2>الهيكل التنظيمي - عرض شجري احترافي</h2>
            <button class="big-btn" onclick="renderTree()">تحديث العرض الشجري</button>
        </div>
        <div id="treeView"></div>
    </div>

    <footer>أكاديمية الزرقاء © 2025 – اسم الرئيس التنفيذي واضح الآن 100%</footer>
</div>

<script>
function openTab(t){
    document.querySelectorAll('.tab-content').forEach(x=>x.classList.remove('active'));
    document.querySelectorAll('.tab').forEach(x=>x.classList.remove('active'));
    document.getElementById(t).classList.add('active');
    document.querySelector(`.tab[onclick="openTab('${t}')"]`).classList.add('active');
    if(t==='tree') renderTree();
}
function save(){localStorage.setItem('alzarkaa_final_2025',document.getElementById('orgChart').innerHTML);}
document.addEventListener('click',e=>{
    const el = e.target.closest('.editable,.name,strong,.box,.local,.subdept');
    if(!el || el.isContentEditable) return;
    el.contentEditable=true; el.focus();
    el.style.outline='3px solid #0b4b8a'; el.style.borderRadius='12px';
    const end=()=>{el.contentEditable=false; el.style.outline=''; save(); renderTree();}
    el.onblur=end; el.onkeydown=ev=>{if(ev.key==='Enter'){ev.preventDefault();el.blur();}}
});

function load(){
    if(localStorage.getItem('alzarkaa_final_2025')){
        document.getElementById('orgChart').innerHTML = localStorage.getItem('alzarkaa_final_2025');
    } else {
        buildFullStructure();
    }
    renderTree();
}

function buildFullStructure(){
    const o = document.getElementById('orgChart');
    o.innerHTML = `
        <div class="level"><div class="box ceo">الشركة القابضة<br>أكاديمية الزرقاء</div><div class="connector"></div>
        <div class="box ceo editable">الرئيس التنفيذي<div class="name editable">د. أحمد بن عبدالله الزرقاء</div></div></div>
        <div class="h-connector"></div>
        <div class="branches" id="centralDepts"></div>
        <div class="h-connector"></div>
        <div class="branches" id="branches"></div>`;

    [["الإدارة المركزية<br>(تسويق، مبيعات، موارد بشرية، IT)","أ. محمد العتيبي"],
     ["الإدارة المالية والمحاسبة","أ. سارة الدوسري"],
     ["إدارة العمليات والجودة","أ. لينا الفهد"]].forEach(d=>addCentral(d[0],d[1]));

    [["الرياض","أ. خالد الشمري",[["قسم التدريب الميداني","ريم الدخيل",[["منسق برامج","سعود الدخيل"]]],["قسم المبيعات","عبدالله المهوس",[]]]],
     ["جدة","أ. فاطمة البقمي",[["قسم التدريب","سارة الغامدي",[]]]],
     ["الدمام","أ. علي الدوسري",[["قسم التدريب","فهد العنزي",[]]]],
     ["أونلاين","أ. مشاري الراجحي",[["قسم المنصة الإلكترونية","يوسف التميمي",[]]]]].forEach(b=>addFullBranch(b[0],b[1],b[2]));

    save();
}

function addCentral(t,m){const d=document.createElement('div');d.className='central-group';d.innerHTML=`<button class="del-btn" onclick="this.parentElement.remove();save();renderTree()">×</button><button class="add-btn" onclick="addPos(this)">+</button><div class="box central editable">${t}</div><div class="name editable">${m}</div>`;document.getElementById('centralDepts').appendChild(d);}
function addFullBranch(c,m,s){const g=document.createElement('div');g.className='branch-group';let h='';s.forEach(x=>{let p='';x[2]?.forEach(y=>p+=`<div class="local editable">${y[0]}<br><span class="name editable">${y[1]}</span></div>`);h+=`<div class="subdept"><button class="del-btn" style="top:8px;right:8px;width:32px;height:32px;" onclick="this.parentElement.remove();save();renderTree()">×</button><button class="add-btn" style="top:8px;left:8px;width:32px;height:32px;" onclick="addPos(this)">+</button><strong class="editable">${x[0]}</strong><br><div class="name editable">${x[1]}</div>${p}</div>`});g.innerHTML=`<button class="del-btn" onclick="this.parentElement.remove();save();renderTree()">×</button><button class="add-btn" onclick="addSub(this)">+</button><div class="box branch editable">أكاديمية الزرقاء - ${c}</div><div class="name editable">${m}</div><div class="subdepts-container">${h}</div><button style="margin-top:20px;background:#2c7ad2;color:white;padding:12px 30px;border-radius:40px;" onclick="addSub(this)">⊕ قسم جديد</button>`;document.getElementById('branches').appendChild(g);}
function addNewBranch(){Swal.fire({title:'فرع جديد',html:'<input id="c" class="swal2-input" placeholder="المدينة"><input id="m" class="swal2-input" placeholder="مدير الفرع">',showCancelButton:true}).then(r=>{if(r.isConfirmed){addFullBranch(document.getElementById('c').value,document.getElementById('m').value||'— مدير —',[]);save();renderTree();}});}
function addCentralDept(){Swal.fire({title:'قسم مركزي',html:'<input id="t" class="swal2-input" placeholder="اسم القسم"><input id="m" class="swal2-input" placeholder="المدير">',showCancelButton:true}).then(r=>{if(r.isConfirmed){addCentral(document.getElementById('t').value,document.getElementById('m').value||'— مدير —');save();renderTree();}});}
function addSub(b){Swal.fire({title:'قسم جديد',html:'<input id="n" class="swal2-input" placeholder="اسم القسم"><input id="m" class="swal2-input" placeholder="مدير القسم">',showCancelButton:true}).then(r=>{if(r.isConfirmed){const s=document.createElement('div');s.className='subdept';s.innerHTML=`<button class="del-btn" style="top:8px;right:8px;width:32px;height:32px;" onclick="this.parentElement.remove();save();renderTree()">×</button><button class="add-btn" style="top:8px;left:8px;width:32px;height:32px;" onclick="addPos(this)">+</button><strong class="editable">${document.getElementById('n').value}</strong><br><div class="name editable">${document.getElementById('m').value||'— مدير —'}</div>`;b.parentElement.querySelector('.subdepts-container').appendChild(s);save();renderTree();}});}
function addPos(b){Swal.fire({title:'منصب جديد',input:'text',inputPlaceholder:'المسمى – الاسم'}).then(r=>{if(r.value){const [j,n='—']=r.value.split(' – ');const e=document.createElement('div');e.className='local editable';e.innerHTML=`${j}<br><span class="name editable">${n.trim()}</span>`;b.parentElement.appendChild(e);save();renderTree();}});}

function renderTree(){
    document.getElementById('treeView').innerHTML = '<div style="padding:200px;text-align:center;color:#666;font-size:24px;">جاري تحميل الرسم الشجري...</div>';
    
    setTimeout(() => {
        const data = {
            'name': 'أكاديمية الزرقاء',
            'title': 'الشركة القابضة',
            'className': 'ceo',
            'children': [{
                'name': document.querySelector('.box.ceo .name')?.innerText.trim() || 'الرئيس التنفيذي',
                'title': 'الرئيس التنفيذي للمجموعة',
                'className': 'ceo',
                'children': [
                    ...Array.from(document.querySelectorAll('#centralDepts .central-group')).map(g => ({
                        'name': g.querySelector('.box.central')?.innerHTML.replace(/<br>/g,' ').trim(),
                        'title': g.querySelector('.name')?.innerText.trim(),
                        'className': 'central'
                    })),
                    {
                        'name': 'الفروع',
                        'className': 'branch',
                        'children': Array.from(document.querySelectorAll('#branches .branch-group')).map(b => ({
                            'name': b.querySelector('.box.branch')?.innerText.trim(),
                            'title': b.querySelector('.name')?.innerText.trim(),
                            'className': 'branch',
                            'children': Array.from(b.querySelectorAll('.subdept')).map(s => ({
                                'name': s.querySelector('strong')?.innerText.trim(),
                                'title': s.querySelector('.name')?.innerText.trim(),
                                'className': 'subdept',
                                'children': Array.from(s.querySelectorAll('.local')).map(l => ({
                                    'name': l.childNodes[0].nodeValue?.trim(),
                                    'title': l.querySelector('.name')?.innerText.trim(),
                                    'className': 'local'
                                }))
                            }))
                        }))
                    }
                ]
            }]
        };

        document.getElementById('treeView').innerHTML = '';
        new OrgChart(document.getElementById('treeView'), {
            chartContainer: '#treeView',
            enableDrag: true,
            pan: true,
            zoom: true,
            direction: 't2b',
            nodeBinding: {field_0: 'name', field_1: 'title'},
            nodeTemplate: function(data) {
                return `<div style="padding:14px;"><div style="font-weight:900;font-size:18px;">${data.name}</div><div style="margin-top:6px;font-size:16px;color:${data.className==='ceo'?'white':'#003c70'};">${data.title || ''}</div></div>`;
            }
        }).loadData(data);
    }, 300);
}

window.onload = load;
</script>
</body>
</html>
