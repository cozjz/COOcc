<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Circle of Creative | Portfolio</title>
  <style>
    :root { --brand:#00897b; }
    * { box-sizing:border-box; }
    body { font-family: system-ui, -apple-system, Segoe UI, Roboto, Noto Sans KR, sans-serif; margin:0; color:#111; background:#fff; }
    header { text-align:center; padding:64px 20px 40px; }
    header h1 { font-size:2rem; letter-spacing:0.08em; margin:0 0 8px; }
    header p { color:#666; margin:0; }

    section { padding:56px 20px; max-width:1000px; margin:auto; }
    h2 { text-align:center; margin:0 0 28px; font-size:1.6rem; }

    .projects { display:grid; grid-template-columns:repeat(auto-fit,minmax(280px,1fr)); gap:20px; }
    .project { border-radius:16px; overflow:hidden; box-shadow:0 2px 10px rgba(0,0,0,.08); background:#fafafa; transition:.25s; }
    .project:hover { transform:translateY(-4px); box-shadow:0 6px 16px rgba(0,0,0,.12); }
    .project img { width:100%; height:200px; object-fit:cover; display:block; }
    .project .meta { padding:16px; }
    .badge { display:inline-block; background:var(--brand); color:#fff; padding:3px 8px; border-radius:12px; font-size:.75rem; margin-right:6px; }

    footer { text-align:center; padding:36px; color:#777; font-size:.9rem; }

    /* Admin floating UI */
    #adminBtn { position:fixed; right:20px; bottom:20px; width:52px; height:52px; border-radius:50%; border:none; background:var(--brand); color:#fff; font-size:22px; cursor:pointer; box-shadow:0 6px 16px rgba(0,0,0,.2); }
    #loginBox, #editorBox { position:fixed; right:20px; bottom:84px; width:320px; max-height:80vh; overflow:auto; background:#fff; border-radius:14px; box-shadow:0 16px 40px rgba(0,0,0,.25); padding:16px; display:none; }
    #loginBox input, #editorBox input, #editorBox textarea { width:100%; padding:10px 12px; border:1px solid #ddd; border-radius:8px; margin-top:6px; }
    #editorBox h4 { margin:10px 0; color:var(--brand); font-size:1rem; }
    .row { display:grid; grid-template-columns:1fr 1fr; gap:10px; }
    .row.single { grid-template-columns:1fr; }
    .toolbar { margin-top:8px; text-align:right; }
    .btn.primary { background:var(--brand); color:#fff; border:none; border-radius:8px; padding:8px 12px; cursor:pointer; }
    hr { border:0; border-top:1px dashed #eee; margin:14px 0; }
  </style>
</head>
<body>
  <header>
    <h1>CIRCLE OF CREATIVE</h1>
    <p>Designing Spaces, Perfecting Sensibility</p>
  </header>

  <section class="hero">
    <h2 id="heroTitleText">공간을 디자인하고, 감성을 완성합니다</h2>
    <p id="heroSubtitleText">Interior Designer | COC Studio</p>
  </section>

  <section id="about">
    <h2>About</h2>
    <p id="aboutText">Circle of Creative는 공간을 통해 감성과 기능이 공존하는 디자인을 제안합니다.</p>
  </section>

  <section id="projects">
    <h2>Selected Works</h2>
    <!-- 지정 프로젝트 미리보기 영역 -->
    <div id="previewMount" class="projects" style="margin-bottom:24px; display:none"></div>
    <div id="projectGrid" class="projects"></div>
  </section>

  <section id="contact">
    <h2>Contact</h2>
    <p id="contactEmailText">📧 contact@circleofcreative.com</p>
    <p id="contactLocationText">📍 Seoul, Republic of Korea</p>
  </section>

  <footer>© 2025 Circle of Creative. All Rights Reserved.</footer>

  <!-- Admin Floating Button -->
  <button id="adminBtn" title="관리자">⚙️</button>

  <!-- Admin: Login -->
  <div id="loginBox">
    <label>관리자 비밀번호</label>
    <input type="password" id="adminPass" placeholder="비밀번호 입력" />
    <div class="toolbar"><button id="loginBtn" class="btn primary" type="button">로그인</button></div>
  </div>

  <!-- Admin: Editor -->
  <div id="editorBox">
    <h4>사이트 설정</h4>
    <div class="row">
      <div>
        <label>상단 헤드라인</label>
        <input id="siteHeroTitle" type="text" placeholder="공간을 디자인하고, 감성을 완성합니다" />
      </div>
      <div>
        <label>상단 서브문구</label>
        <input id="siteHeroSubtitle" type="text" placeholder="Interior Designer | COC Studio" />
      </div>
    </div>
    <div class="row single">
      <div>
        <label>About 콘텐츠</label>
        <textarea id="siteAbout" placeholder="About 섹션 내용을 입력"></textarea>
      </div>
    </div>
    <div class="row">
      <div>
        <label>Contact 이메일</label>
        <input id="siteContactEmail" type="text" placeholder="contact@circleofcreative.com" />
      </div>
      <div>
        <label>Contact 위치</label>
        <input id="siteContactLocation" type="text" placeholder="Seoul, Republic of Korea" />
      </div>
    </div>
    <div class="toolbar">
      <button id="saveSettingsBtn" class="btn primary" type="button">사이트 설정 저장</button>
    </div>
    <hr />

    <h4>지정 프로젝트</h4>
    <div class="row">
      <div>
        <label>프로젝트 이름</label>
        <input id="projectName" type="text" placeholder="예: Residential Villa" />
      </div>
      <div>
        <label>프로젝트 위치</label>
        <input id="projectLocation" type="text" placeholder="예: Riyadh, KSA" />
      </div>
    </div>
    <div class="row single">
      <div>
        <label>프로젝트 설명</label>
        <textarea id="projectDescription" placeholder="프로젝트 설명을 입력하세요"></textarea>
      </div>
    </div>
    <div class="toolbar">
      <button id="saveProjectBtn" class="btn primary" type="button">프로젝트 저장</button>
    </div>

    <hr />
    <h4>파일 내보내기</h4>
    <div class="toolbar">
      <button id="exportHtmlBtn" class="btn primary" type="button">index.html 다운로드</button>
    </div>
  </div>

  <script>
    // ====== Constants & Elements ======
    const ADMIN_PASSWORD = 'coc-admin';
    const META_KEY = 'coc_site_meta_v1';

    const heroTitleText = document.getElementById('heroTitleText');
    const heroSubtitleText = document.getElementById('heroSubtitleText');
    const aboutText = document.getElementById('aboutText');
    const contactEmailText = document.getElementById('contactEmailText');
    const contactLocationText = document.getElementById('contactLocationText');

    const adminBtn = document.getElementById('adminBtn');
    const loginBox = document.getElementById('loginBox');
    const editorBox = document.getElementById('editorBox');

    const loginBtn = document.getElementById('loginBtn');
    const passInput = document.getElementById('adminPass');

    const siteHeroTitle = document.getElementById('siteHeroTitle');
    const siteHeroSubtitle = document.getElementById('siteHeroSubtitle');
    const siteAbout = document.getElementById('siteAbout');
    const siteContactEmail = document.getElementById('siteContactEmail');
    const siteContactLocation = document.getElementById('siteContactLocation');
    const saveSettingsBtn = document.getElementById('saveSettingsBtn');

    const projectNameInput = document.getElementById('projectName');
    const projectLocationInput = document.getElementById('projectLocation');
    const projectDescriptionInput = document.getElementById('projectDescription');
    const saveProjectBtn = document.getElementById('saveProjectBtn');
    const exportHtmlBtn = document.getElementById('exportHtmlBtn');

    const previewMount = document.getElementById('previewMount');

    // ====== Helpers ======
    function saveMeta(meta){
      try { localStorage.setItem(META_KEY, JSON.stringify(meta)); }
      catch(e){ console.error('Meta save error', e); alert('사이트 설정 저장 중 오류가 발생했습니다.'); }
    }
    function loadMeta(){
      try {
        const raw = localStorage.getItem(META_KEY);
        return raw ? JSON.parse(raw) : null;
      } catch(e){ console.error(e); return null; }
    }
    function applyMetaToDOM(meta){
      if(!meta) return;
      if(meta.heroTitle !== undefined) heroTitleText.textContent = meta.heroTitle || '';
      if(meta.heroSubtitle !== undefined) heroSubtitleText.textContent = meta.heroSubtitle || '';
      if(meta.about !== undefined) aboutText.textContent = meta.about || '';
      if(meta.contactEmail !== undefined) contactEmailText.textContent = '📧 ' + (meta.contactEmail || '');
      if(meta.contactLocation !== undefined) contactLocationText.textContent = '📍 ' + (meta.contactLocation || '');
    }

    // ====== Admin UI ======
    adminBtn.addEventListener('click', () => {
      // 토글: 로그인 박스가 열려있으면 닫고, 닫혀있으면 열기
      loginBox.style.display = (loginBox.style.display === 'block') ? 'none' : 'block';
      editorBox.style.display = 'none';
    });

    loginBtn.addEventListener('click', () => {
      if(passInput.value === ADMIN_PASSWORD){
        loginBox.style.display = 'none';
        editorBox.style.display = 'block';
        const meta = loadMeta() || {
          heroTitle: heroTitleText.textContent.trim(),
          heroSubtitle: heroSubtitleText.textContent.trim(),
          about: aboutText.textContent.trim(),
          contactEmail: contactEmailText.textContent.replace('📧','').trim(),
          contactLocation: contactLocationText.textContent.replace('📍','').trim()
        };
        siteHeroTitle.value = meta.heroTitle || '';
        siteHeroSubtitle.value = meta.heroSubtitle || '';
        siteAbout.value = meta.about || '';
        siteContactEmail.value = meta.contactEmail || '';
        siteContactLocation.value = meta.contactLocation || '';
      } else {
        alert('비밀번호가 올바르지 않습니다.');
      }
    });

    saveSettingsBtn.addEventListener('click', () => {
      const meta = {
        heroTitle: siteHeroTitle.value.trim(),
        heroSubtitle: siteHeroSubtitle.value.trim(),
        about: siteAbout.value.trim(),
        contactEmail: siteContactEmail.value.trim(),
        contactLocation: siteContactLocation.value.trim()
      };
      saveMeta(meta);
      applyMetaToDOM(meta);
      alert('사이트 설정이 저장되었습니다.');
    });

    // ====== Designated Project Preview ======
    function renderPreviewCard(name, location, description){
      if(!name) return;
      previewMount.style.display = 'grid';
      previewMount.innerHTML = '';
      const card = document.createElement('article');
      card.className = 'project';
      const svg = encodeURI("<svg xmlns='http://www.w3.org/2000/svg' width='1200' height='800'><defs><linearGradient id='g' x1='0' y1='0' x2='1' y2='1'><stop offset='0%' stop-color='%2300897b'/><stop offset='100%' stop-color='%2300b3a5'/></linearGradient></defs><rect fill='url(%23g)' width='100%' height='100%'/><text x='50%' y='50%' dominant-baseline='middle' text-anchor='middle' fill='white' font-family='Arial' font-size='56'>PREVIEW</text></svg>");
      const ph = 'data:image/svg+xml;utf8,' + svg;
      card.innerHTML =
        '<img src="' + ph + '" alt="preview">' +
        '<div class="meta">' +
          '<h3>' + name + '</h3>' +
          '<p>' + (description || '') + '</p>' +
          '<div class="badges">' +
            (location ? '<span class="badge">' + location + '</span>' : '') +
            '<span class="badge">PREVIEW</span>' +
          '</div>' +
        '</div>';
      previewMount.appendChild(card);
    }

    saveProjectBtn.addEventListener('click', () => {
      const name = projectNameInput.value.trim();
      const location = projectLocationInput.value.trim();
      const description = projectDescriptionInput.value.trim();
      if(!name){ alert('프로젝트 이름을 입력하세요.'); return; }
      renderPreviewCard(name, location, description);
      document.getElementById('projects').scrollIntoView({ behavior:'smooth', block:'start' });
      alert('지정 프로젝트 미리보기가 갱신되었습니다.');
    });

    // ====== Initial meta apply ======$1);

    // ====== Export current page as index.html ======
    function downloadFile(name, content){
      const blob = new Blob([content], {type:'text/html;charset=utf-8'});
      const a = document.createElement('a');
      a.href = URL.createObjectURL(blob);
      a.download = name;
      document.body.appendChild(a);
      a.click();
      URL.revokeObjectURL(a.href);
      a.remove();
    }
    exportHtmlBtn.addEventListener('click', ()=>{
      try{
        const html = '<!DOCTYPE html>
' + document.documentElement.outerHTML;
        downloadFile('index.html', html);
      }catch(e){
        console.error(e);
        alert('다운로드 중 문제가 발생했습니다.');
      }
    }); if(meta) applyMetaToDOM(meta); })();
  </script>
</body>
</html>
