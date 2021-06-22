<template>
  <footer class="footer">
    <div class="container-fluid">
      <ul class="nav">
        <li class="nav-item">
          <a
            href="https://www.ute.edu.ec"
            target="_blank"
            rel="noopener"
            class="nav-link"
          >
            Nosotros
          </a>
        </li>
      </ul>
      <div class="copyright">
        &copy; {{ year }}, Hecho con <i class="tim-icons icon-heart-2"></i> by
        
        <a
          href="#"
          target="_blank"
          rel="noopener"
          >Andrés Quishpe</a
        >
      </div>
    </div>
  </footer>
</template>
<script>
export default {
  data() {
    return {
      year: new Date().getFullYear()
    };
  }
};
</script>
<style></style>
