---
layout: default
title: Ask a Philosopher
---

<div class="divider"></div>

<h2 class="section-title">Ask a Philosopher</h2>

<p class="center-paragraph">
  Choose a theme, pick a philosopher, leave your email, and ask your question.
  I’ll reply to you by email.
</p>

<form id="ask-form" class="ask-form" action="https://formspree.io/f/mqayjnrj" method="POST" novalidate>

  <!-- 主题下拉 -->
  <label for="theme">Choose a theme</label>
  <select id="theme" name="theme" required>
    <option value="" disabled selected>— Select a theme —</option>
    <option>Art</option>
    <option>Education</option>
    <option>Ethics</option>
    <option>Gender</option>
    <option>Knowledge</option>
    <option>Law</option>
    <option>Meaning &amp; Existence</option>
    <option>Mind &amp; Self</option>
    <option>Politics</option>
    <option>Religion &amp; Faith</option>
    <option>Science</option>
    <option>Society</option>
    <option>Technology</option>
  </select>

  <!-- 哲学家下拉 -->
  <label for="philosopher">Pick a philosopher</label>
  <select id="philosopher" name="philosopher" required>
    <option value="" disabled selected>— Select a philosopher —</option>
    <option>Aristotle</option>
    <option>Confucius</option>
    <option>David Hume</option>
    <option>Edmund Husserl</option>
    <option>Friedrich Nietzsche</option>
    <option>George Berkeley</option>
    <option>Gottfried Wilhelm Leibniz</option>
    <option>Hannah Arendt</option>
    <option>Immanuel Kant</option>
    <option>Jean-Paul Sartre</option>
    <option>John Locke</option>
    <option>Mary Astell</option>
    <option>Mary Wollstonecraft</option>
    <option>Maurice Merleau-Ponty</option>
    <option>Plato</option>
    <option>René Descartes</option>
    <option>Simone de Beauvoir</option>
    <option>Zhuangzi</option>
    <option>Anyone — surprise me!</option>
  </select>

  <!-- 用户问题 -->
  <label for="question">Share your question</label>
  <textarea id="question" name="question" rows="6" placeholder="Write your question here…" required></textarea>

   <!-- Email -->
  <label for="email">Please leave your email address below so I can reply to your question directly. Your address is used only for this conversation.</label>
  <input id="email" name="email" type="email" placeholder="you@example.com" required>

   <!-- 蜜罐反垃圾（不要改 name 值） -->
  <input type="text" name="_gotcha" style="display:none">

  <!-- 成功后停留本页（由 JS 控制），这里留空即可 -->
  <input type="hidden" name="_redirect" value="">

  <button type="submit" class="ask-submit">Send</button>
  

 <!-- 提交状态提示 -->
  <p id="ask-status" style="display:none; margin-top:10px;"></p>
</form>

 

<div class="divider"></div>

<script>
  (function(){
    const form = document.getElementById('ask-form');
    const status = document.getElementById('ask-status');

    function showStatus(msg, ok){
      status.textContent = msg;
      status.style.display = 'block';
      status.style.color = ok ? '#1B3A57' : '#D95F1C';
    }

    form.addEventListener('submit', async function(e){
      e.preventDefault();
      status.style.display = 'none';

      // 前端校验（避免空提交）
      const theme = document.getElementById('theme').value;
      const philosopher = document.getElementById('philosopher').value;
      const email = document.getElementById('email').value.trim();
      const question = document.getElementById('question').value.trim();

      if(!theme || !philosopher || !email || !question){
        showStatus('⚠️ Please complete all fields.', false);
        return;
      }

      // 发送
      const data = new FormData(form);
      try {
        const res = await fetch(form.action, {
          method: 'POST',
          headers: { 'Accept': 'application/json' },
          body: data
        });
        if (res.ok) {
          form.reset();
          showStatus('✅ Submitted!', true);
        } else {
          showStatus('⚠️ Submission failed. Please try again or email me directly.', false);
        }
      } catch (err) {
        showStatus('⚠️ Network error. Please try again later.', false);
      }
    });
  })();
</script>
