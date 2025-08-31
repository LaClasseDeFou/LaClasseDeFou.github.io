<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Admin — Gestion classes & chats</title>
  <style>
    :root{ --bg:linear-gradient(135deg,#6a11cb,#2575fc); --card:rgba(255,255,255,0.04); --muted:#cbd5f6; --accent:#ffd369; --radius:12px;}
    *{box-sizing:border-box}
    body{margin:0;font-family:Inter,Arial;background:var(--bg);color:white;-webkit-font-smoothing:antialiased}
    .wrap{min-height:100vh;display:flex;align-items:flex-start;justify-content:center;padding:28px}
    .card{width:100%;max-width:1100px;background:var(--card);padding:18px;border-radius:var(--radius);box-shadow:0 12px 40px rgba(0,0,0,0.4)}
    h1{margin:0 0 10px 0}
    .row{display:flex;gap:12px;align-items:center}
    .col{display:flex;flex-direction:column;gap:8px}
    input,select,textarea{padding:10px;border-radius:8px;border:1px solid rgba(255,255,255,0.06);background:rgba(0,0,0,0.12);color:white}
    button{padding:8px 12px;border-radius:8px;border:none;background:linear-gradient(90deg,#7f5af0,#6a11cb);color:white;cursor:pointer}
    .btn-light{background:transparent;border:1px solid rgba(255,255,255,0.06)}
    .grid{display:grid;grid-template-columns:1fr 1fr;gap:12px;margin-top:12px}
    .box{padding:12px;border-radius:10px;background:rgba(0,0,0,0.12);min-height:120px}
    .messages{height:420px; overflow:auto; padding:10px; border-radius:8px; background:rgba(0,0,0,0.06)}
    .msg{padding:8px;border-radius:8px;margin-bottom:8px;background:rgba(255,255,255,0.03)}
    .meta{font-size:12px;color:var(--muted);margin-bottom:6px}
    .danger{background:rgba(255,107,107,0.12);color:#ffb4b4;padding:8px;border-radius:8px}
    small{color:var(--muted)}
  </style>
</head>
<body>
  <div class="wrap">
    <div class="card">
      <h1>Admin — Gestion des classes & chats</h1>
      <div class="row" style="justify-content:space-between;align-items:center;margin-bottom:8px">
        <div><small>Seul un compte admin peut accéder à cette page.</small></div>
        <div>
          <button id="backBtn" class="btn btn-light">Retour</button>
          <button id="logoutBtn" class="btn btn-light">Se déconnecter</button>
        </div>
      </div>

      <div class="grid">
        <div class="col">
          <div class="box">
            <div style="display:flex;gap:8px;align-items:center;margin-bottom:8px">
              <label for="classSelect"><strong>Classe :</strong></label>
              <select id="classSelect" style="min-width:140px">
                <option value="">-- Choisir --</option>
                <option>6A</option><option>6B</option><option>6C</option><option>6D</option><option>6E</option>
                <option>5A</option><option>5B</option><option>4A</option><option>3A</option><option>3E</option>
              </select>
              <button id="loadChat" class="btn">Charger chat</button>
            </div>
            <div class="messages" id="messages"></div>
          </div>
        </div>

        <div class="col">
          <div class="box">
            <div style="display:flex;gap:8px;align-items:center;margin-bottom:8px">
              <input id="searchEmail" placeholder="Chercher utilisateur par email" style="flex:1" />
              <button id="searchBtn" class="btn">Chercher</button>
            </div>
            <div id="userInfo">Aucun utilisateur sélectionné.</div>

            <div id="editArea" style="display:none;margin-top:10px">
              <div style="display:flex;gap:8px;margin-bottom:8px">
                <input id="editPseudo" placeholder="Pseudo (users doc)" style="flex:1" />
                <input id="editClasse" placeholder="Classe (ex 6A)" style="width:120px" />
              </div>
              <div style="display:flex;gap:8px">
                <button id="saveUser" class="btn">Enregistrer</button>
                <button id="deleteUserDoc" class="btn btn-light">Suppr. doc user</button>
              </div>
              <div id="editMsg" style="margin-top:8px"></div>
            </div>
          </div>

          <div class="box" style="margin-top:12px">
            <strong>Actions globales</strong>
            <div style="display:flex;gap:8px;margin-top:8px">
              <button id="refreshBtn" class="btn btn-light">Rafraîchir</button>
            </div>
            <div id="adminNote" style="margin-top:8px;color:var(--muted)"><small>Modifier le champ <code>classe</code> mettra à jour le document <code>users/{uid}</code>. Pour modifier l'auth.displayName il faut utiliser Admin SDK (script local).</small></div>
          </div>
        </div>
      </div>
    </div>
  </div>

<script type="module">
  import { initializeApp } from "https://www.gstatic.com/firebasejs/10.13.2/firebase-app.js";
  import { getAuth, onAuthStateChanged, signOut } from "https://www.gstatic.com/firebasejs/10.13.2/firebase-auth.js";
  import {
    getFirestore, collection, query, where, orderBy, onSnapshot,
    getDocs, doc, updateDoc, deleteDoc, getDoc
  } from "https://www.gstatic.com/firebasejs/10.13.2/firebase-firestore.js";

  const firebaseConfig = {
    apiKey: "AIzaSyDYPGjiUNLU9nzPNWVDfWMXQ7zYeE7VRtI",
    authDomain: "laclassedefou.firebaseapp.com",
    projectId: "laclassedefou",
    storageBucket: "laclassedefou.firebasestorage.app",
    messagingSenderId: "625518146786",
    appId: "1:625518146786:web:1ccbf39c23199b0dda1abb",
    measurementId: "G-DP9HJXJGTC"
  };

  const app = initializeApp(firebaseConfig);
  const auth = getAuth(app);
  const db = getFirestore(app);

  const classSelect = document.getElementById('classSelect');
  const loadChat = document.getElementById('loadChat');
  const messagesEl = document.getElementById('messages');
  const backBtn = document.getElementById('backBtn');
  const logoutBtn = document.getElementById('logoutBtn');
  const searchEmail = document.getElementById('searchEmail');
  const searchBtn = document.getElementById('searchBtn');
  const userInfo = document.getElementById('userInfo');
  const editArea = document.getElementById('editArea');
  const editPseudo = document.getElementById('editPseudo');
  const editClasse = document.getElementById('editClasse');
  const saveUser = document.getElementById('saveUser');
  const deleteUserDoc = document.getElementById('deleteUserDoc');
  const editMsg = document.getElementById('editMsg');
  const refreshBtn = document.getElementById('refreshBtn');

  let unsubscribeMessages = null;
  let currentClass = '';
  let selectedUser = null;

  onAuthStateChanged(auth, async user => {
    if(!user) { location.href = 'login.html'; return; }
    await user.getIdToken(true);
    const token = await user.getIdTokenResult();
    if(!token.claims || !token.claims.admin) { alert('Accès admin requis. Redirection.'); location.href='home.html'; return; }
  });

  backBtn.addEventListener('click', ()=> location.href = 'home.html');
  logoutBtn.addEventListener('click', ()=> signOut(auth).then(()=> location.href='login.html'));

  function renderMessages(snapshotDocs) {
    messagesEl.innerHTML = '';
    snapshotDocs.forEach(d => {
      const m = d.data();
      const id = d.id;
      const div = document.createElement('div');
      div.className = 'msg';
      const meta = document.createElement('div'); meta.className = 'meta';
      const name = m.displayName || m.pseudo || m.email || 'Anonyme';
      const time = m.createdAt && m.createdAt.toDate ? new Date(m.createdAt.toDate()).toLocaleString() : '';
      meta.textContent = `${name} • ${time} • id:${id}`;
      const body = document.createElement('div'); body.textContent = m.text || '(pas de texte)';
      const actions = document.createElement('div'); actions.style.marginTop = '8px';
      const delBtn = document.createElement('button'); delBtn.textContent = 'Supprimer'; delBtn.className = 'btn btn-light';
      delBtn.onclick = async () => {
        if(!confirm('Supprimer ce message ?')) return;
        try{ await deleteDoc(doc(db,'messages',id)); }catch(e){ alert('Erreur suppression'); console.error(e); }
      };
      actions.appendChild(delBtn);
      div.appendChild(meta); div.appendChild(body); div.appendChild(actions);
      messagesEl.appendChild(div);
    });
    messagesEl.scrollTop = messagesEl.scrollHeight;
  }

  loadChat.addEventListener('click', async ()=>{
    const classe = (classSelect.value || '').trim();
    if(!classe){ alert('Choisis une classe'); return; }
    currentClass = classe;
    if(unsubscribeMessages) unsubscribeMessages();
    const q = query(collection(db,'messages'), where('classe','==',classe), orderBy('createdAt'));
    unsubscribeMessages = onSnapshot(q, snap => { renderMessages(snap.docs); });
  });

  searchBtn.addEventListener('click', async ()=>{
    const email = (searchEmail.value||'').trim();
    if(!email){ userInfo.innerText = 'Renseigne un email.'; return; }
    userInfo.innerHTML = '<small>Recherche...</small>';
    try{
      const q = query(collection(db,'users'), where('email','==', email));
      const snap = await getDocs(q);
      if(snap.empty){ userInfo.innerHTML = `<div>Aucun user doc trouvé pour ${email}.</div>`; selectedUser = null; editArea.style.display='none'; return; }
      const d = snap.docs[0];
      selectedUser = { uid: d.id, data: d.data() };
      userInfo.innerHTML = `<div><strong>UID:</strong> ${selectedUser.uid}<br><strong>Email:</strong> ${selectedUser.data.email || ''}<br><strong>Pseudo:</strong> ${selectedUser.data.pseudo || ''}<br><strong>Classe:</strong> ${selectedUser.data.classe || '(aucune)'}</div>`;
      editPseudo.value = selectedUser.data.pseudo || '';
      editClasse.value = selectedUser.data.classe || '';
      editArea.style.display = 'block';
      editMsg.innerText = '';
    }catch(e){ console.error(e); userInfo.innerText = 'Erreur lors de la recherche.'; selectedUser = null; editArea.style.display='none'; }
  });

  saveUser.addEventListener('click', async ()=>{
    if(!selectedUser){ editMsg.innerText = 'Aucun utilisateur sélectionné.'; return; }
    const newPseudo = (editPseudo.value||'').trim();
    const newClasse = (editClasse.value||'').trim();
    editMsg.innerText = 'Enregistrement...';
    try{
      await updateDoc(doc(db,'users', selectedUser.uid), { pseudo: newPseudo, classe: newClasse });
      editMsg.innerText = 'Modifications enregistrées.';
    }catch(e){ console.error(e); editMsg.innerText = 'Erreur lors de l\\'enregistrement.'; }
  });

  deleteUserDoc.addEventListener('click', async ()=>{
    if(!selectedUser) return;
    if(!confirm('Supprimer le document utilisateur (users/{uid}) ? Cela ne supprime pas le compte auth.')) return;
    try{ await deleteDoc(doc(db,'users',selectedUser.uid)); userInfo.innerText = 'Document supprimé.'; editArea.style.display='none'; selectedUser = null; }
    catch(e){ console.error(e); userInfo.innerText = 'Erreur suppression.'; }
  });

  refreshBtn.addEventListener('click', ()=> location.reload());
</script>
</body>
</html>
