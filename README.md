
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Mrit education- by Subham</title>
<style>
:root {
  --bg: #000;
  --text: #fff;
  --accent: #FFD700;
  --muted: #ccc;
  --card-bg: #111;
}
* {box-sizing: border-box;}
body {font-family: Inter, system-ui, sans-serif; margin:0; color: var(--text); background: var(--bg);}
header {display:flex;align-items:center;justify-content:space-between;padding:16px 24px;background:#111;border-bottom:2px solid var(--accent);}
.logo {display:flex;gap:12px;align-items:center;}
.logo .mark {width:44px;height:44px;border-radius:8px;background:var(--accent);display:flex;align-items:center;justify-content:center;color:#000;font-weight:700;}
nav a {margin-left:16px;color:var(--text);text-decoration:none;}
nav a:hover {color:var(--accent);}
.hero {padding:20px 24px;display:grid;grid-template-columns:1fr 320px;gap:20px;}
.search-box {background:var(--card-bg);padding:18px;border-radius:12px;border:1px solid var(--accent);}
.search-row {display:flex;gap:10px;}
input[type=text] {flex:1;padding:12px 14px;border-radius:8px;border:1px solid var(--accent);font-size:15px;background:#000;color:#fff;}
button.primary {background:var(--accent);color:#000;padding:10px 12px;border-radius:8px;border:0;cursor:pointer;font-weight:bold;}
.filters {margin-top:12px;display:flex;gap:8px;flex-wrap:wrap;}
.chip {padding:8px 10px;background:var(--card-bg);border:1px solid var(--accent);border-radius:999px;font-size:14px;color:var(--text);cursor:pointer;}
.chip.active {background:var(--accent);color:#000;border-color:var(--accent);}
.ticker {height:120px;overflow:hidden;position:relative;}
.ticker-item {padding:8px 6px;border-bottom:1px dashed var(--accent);}
main {padding:18px 24px; display:none;}
.grid {display:grid;grid-template-columns:repeat(auto-fill,minmax(240px,1fr));gap:14px;}
.card {background:var(--card-bg);padding:14px;border-radius:10px;border:1px solid var(--accent);}
.card h3 {margin:0 0 8px 0;font-size:16px;color:var(--accent);}
.meta {font-size:13px;color:var(--muted);margin-bottom:8px;}
.card p {font-size:14px;color:#fff;margin:0 0 12px 0;line-height:1.4;white-space:pre-line;}
.card img {width:100%;border-radius:6px;margin:8px 0;}
#loginPage {padding:20px; max-width:400px; margin:100px auto; text-align:center;}
#loginPage input{width:100%;padding:8px;margin:12px 0;font-size:16px;}
#loginPage button{background:var(--accent);color:#000;padding:10px 12px;border-radius:8px;border:0;cursor:pointer;font-weight:bold;}
#loginError{color:red;margin-top:8px;}
@media (max-width:880px){.hero{grid-template-columns:1fr;}.ticker{order:2;}}
</style>
</head>
<body>
<header>
<div class="logo">
  <div class="mark">MRIT</div>
  <div class="text">
    <div style="font-weight:700">MRIT EDUACTION</div>
    <div style="font-size:12px;color:var(--muted)">Notes | GK | Current Affairs</div>
  </div>
</div>
<nav>
  <a href="#">Home</a>
  <a href="#notes">Notes</a>
  <a href="#gk">GK</a>
  <a href="#about">About Mrit</a>
</nav>
</header>

<div id="loginPage">
<h2 style="color:var(--accent)">Enter Access Code</h2>
<input type="password" id="accessCode" placeholder="Enter code here" />
<button onclick="checkCode()">Unlock</button>
<div id="loginError"></div>
</div>

<section class="hero">
  <div class="search-box">
    <h2 style="margin:0 0 8px 0">Search Notes & GK</h2>
    <div class="search-row">
      <input id="searchInput" type="text" placeholder="Search topic..." />
      <button id="searchBtn" class="primary">Search</button>
    </div>
    <div class="filters" id="categoryFilters"></div>
  </div>

  <aside class="ticker">
    <h3 style="margin:0 0 8px 0">Latest GK / Current Affairs</h3>
    <div id="newsTicker"></div>
  </aside>
</section>

<main>
<h3 id="notes">All Notes</h3>
<div class="grid" id="notesGrid"></div>
</main>

<footer style="padding:18px 24px;border-top:1px solid var(--accent);color:var(--muted);">
Made with ❤️ by Subham Ranjan Singh 
</footer>

<script>
const TEACHER_CODE = '495677';
function checkCode(){
  const input = document.getElementById('accessCode').value.trim();
  if(input === TEACHER_CODE){
    document.getElementById('loginPage').style.display='none';
    document.querySelector('main').style.display='block';
  } else {
    document.getElementById('loginError').textContent='Incorrect code. Try again.';
  }
}

// Sample notes and GK
const NOTES=[
{id:1,title:"Introduction to Arrays",category:"Computer Science",type:"note",content:`In computer science, an array is a fundamental data structure that stores a collection of elements, typically of the same data type, in contiguous memory locations. Each element is identified by an index, a number that allows direct access to the element's value. Arrays are linear, ordered collections that are essential for implementing other data structures and solving various programming problems`,image:null},
{id:2,title:"Linked List Concepts",category:"Computer Science",type:"note",content:`A linked list in Java is a dynamic linear data structure where elements, called nodes, are not stored in contiguous memory locations. Instead, each node contains two parts: the data it holds and a reference (or link) to the next node in the sequence. In the case of a doubly linked list, which Java's LinkedList class implements, each node also contains a reference to the previous node.`,image:null},
{id:3,title:"Stack & Queue",category:"Computer Science",type:"note",content:`A stack is a data structure that operates on a Last-In, First-Out (LIFO) principle, like a stack of plates, where the last item added is the first one removed. In contrast, a queue is a data structure that follows a First-In, First-Out (FIFO) principle, like a line of people, where the first item added is the first one removed. Stacks are used for tasks like function call management and expression evaluation, while queues are used for task scheduling and print spooling`,image:null},
{id:4,title:"GK: India Rivers",category:"GK",type:"gk",content:`Ganga, Yamuna, Godavari, Krishna, Narmada - states and facts.`,image:null},
{id:5,title:"Current Affairs: Climate Summit",category:"Current Affairs",type:"gk",content:`Summary of latest international climate summit outcomes.`,image:null}
];
const categories = ['All', ...Array.from(new Set(NOTES.map(n=>n.category)))];
const filtersEl = document.getElementById('categoryFilters');
const grid = document.getElementById('notesGrid');
const searchInput = document.getElementById('searchInput');
categories.forEach((c,i)=>{
  const chip=document.createElement('div');
  chip.className='chip'+(i===0?' active':'');
  chip.textContent=c;
  chip.addEventListener('click',()=>{document.querySelectorAll('.chip').forEach(x=>x.classList.remove('active')); chip.classList.add('active'); renderNotes();});
  filtersEl.appendChild(chip);
});

function renderNotes(filterText=''){
  const activeCat = document.querySelector('.chip.active').textContent;
  const q = filterText.trim().toLowerCase();
  grid.innerHTML='';
  const filtered = NOTES.filter(n=>{
    if(activeCat!=='All' && n.category!==activeCat) return false;
    if(!q) return true;
    return (n.title+' '+n.content+' '+n.category).toLowerCase().includes(q);
  });
  if(filtered.length===0){ grid.innerHTML='<div style="grid-column:1/-1;color:var(--muted)">No results found.</div>'; return;}
  filtered.forEach(n=>{
    const card=document.createElement('article'); card.className='card';
    card.innerHTML=`<h3>${n.title}</h3><div class="meta">${n.category} • ${n.type}</div>${n.image?`<img src='${n.image}' alt='note image'/>`:''}<p>${n.content}</p>`;
    grid.appendChild(card);
  });
}
searchInput.addEventListener('keydown',e=>{if(e.key==='Enter') renderNotes(searchInput.value);});
renderNotes();

// Sample GK / Current Affairs ticker
const newsTicker = document.getElementById('newsTicker');
const NEWS = [
"India celebrates Independence Day on 15th August.",
"Global climate summit updates released.",
"New education policy implemented in schools.",
"SpaceX launches new satellite into orbit."
];
NEWS.forEach(item=>{
  const div=document.createElement('div'); div.className='ticker-item'; div.textContent=item;
  newsTicker.appendChild(div);
});
</script>
</body>
</html>
