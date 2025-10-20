---
layout: default
title: Ask a Philosopher
---

<div class="divider"></div>

<h2 class="section-title">Ask a Philosopher</h2>

<p class="center-paragraph">
  Choose a theme, pick a philosopher, and share your question. Your submission opens a public thread
  (GitHub Issue) where I can reply and you can follow up.
</p>

<form id="ask-form" class="ask-form" action="https://formspree.io/f/mqayjnrj" method="POST">

  <!-- 主题下拉 -->
  <label for="theme">Choose a theme</label>
  <select id="theme" name="theme" required>
    <option value="" disabled selected>— Select a theme —</option>
    <option>Ethics</option>
    <option>Politics</option>
    <option>Knowledge</option>
    <option>Art</option>
    <option>Science</option>
    <option>Technology</option>
    <option>Education</option>
    <option>Gender</option>
    <option>Law</option>
    <option>Society</option>
    <option>Religion &amp; Faith</option>
    <option>Mind &amp; Self</option>
    <option>Meaning &amp; Existence</option>
  </select>

  <!-- 哲学家下拉 -->
  <label for="philosopher">Pick a philosopher</label>
  <select id="philosopher" name="philosopher" required>
    <option value="" disabled selected>— Select a philosopher —</option>
    <option>Plato</option>
    <option>Aristotle</option>
    <option>Confucius</option>
    <option>Zhuangzi</option>
    <option>René Descartes</option>
    <option>John Locke</option>
    <option>George Berkeley</option>
    <option>Gottfried Wilhelm Leibniz</option>
    <option>David Hume</option>
    <option>Immanuel Kant</option>
    <option>Mary Astell</option>
    <option>Mary Wollstonecraft</option>
    <option>Friedrich Nietzsche</option>
    <option>Edmund Husserl</option>
    <option>Jean-Paul Sartre</option>
    <option>Maurice Merleau-Ponty</option>
    <option>Simone de Beauvoir</option>
    <option>Hannah Arendt</option>
    <option>Anyone — surprise me!</option>
  </select>

  <!-- 用户问题 -->
  <label for="question">Share your question</label>
  <textarea id="question" name="question" rows="6" placeholder="Write your question here…" required></textarea>

  <button type="submit" class="ask-submit">Open Public Thread</button>
  <p class="ask-hint">
    Prefer email? <a href="mailto:yourname@example.com?subject=Ask%20a%20Philosopher&body=Theme:%20%0APhilosopher:%20%0AQuestion:%20"
    class="inline-link">Email me your question</a>.
  </p>


  <p class="ask-hint">
    Submitting will open a new tab to create a public thread on GitHub. You can subscribe to updates and I will reply there.
  </p>
</form>

<div class="divider"></div>

<script>
  (function () {
    // TODO: 把下面的用户名换成你的 GitHub 用户名
    const GITHUB_USER = 'aileencluo'; // ←← 修改这里（如与你用户名不同）
    const REPO = 'aileencluo.github.io'; // 通常就是你的 Pages 仓库名

    const form = document.getElementById('ask-form');
    form.addEventListener('submit', function (e) {
      e.preventDefault();

      const theme = document.getElementById('theme').value;
      const philosopher = document.getElementById('philosopher').value;
      const question = document.getElementById('question').value;

      // Issue 标题与正文（可按需调整格式）
      const title = `[Ask a Philosopher] ${theme} — ${philosopher}`;
      const body =
`**Theme:** ${theme}
**Philosopher:** ${philosopher}

**Question:**
${question}

---

*Submitted via website: https://${GITHUB_USER}.github.io/*`;

      // 可选：给 Issue 加标签（如果仓库设置了对应标签）
      const labels = encodeURIComponent('Ask a Philosopher');

      const url =
        `https://github.com/${GITHUB_USER}/${REPO}/issues/new?` +
        `title=${encodeURIComponent(title)}` +
        `&body=${encodeURIComponent(body)}` +
        `&labels=${labels}`;

      window.open(url, '_blank', 'noopener'); // 新标签打开 GitHub 新 issue 页面
    });
  })();
</script>
