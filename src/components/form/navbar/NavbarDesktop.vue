<template>
    <nav class="professional-navbar" :class="{ scrolled: isScrolled }">
      <div class="navbar-container">
        <router-link to="/" class="navbar-brand">
          <div class="logo-container">
            <img src="@/assets/imagens/LogoNav.png" alt="Logo" class="logo-image main-logo">
          </div>
        </router-link>

        <button class="menu-toggle" @click="toggleMenu" :class="{ active: isMenuOpen }">
          <span></span>
          <span></span>
          <span></span>
        </button>

        <div class="nav-menu" :class="{ active: isMenuOpen }">
          <ul class="nav-links">
            <li class="nav-item" :class="{ active: activeSection === 'inicio' }">
              <router-link class="nav-link" to="/" @click="setActiveSection('inicio')">
                <span>Início</span>
              </router-link>
            </li>
            <li class="nav-item" :class="{ active: activeSection === 'depoimentos' }">
              <router-link class="nav-link" to="/Depoimentos" @click="setActiveSection('depoimentos')" custom v-slot="{ navigate }">
                <a @click="handleNavigation(navigate, 'depoimentos')" class="nav-link">
                  <span>Depoimentos</span>
                </a>
              </router-link>
            </li>
            <li class="nav-item" :class="{ active: activeSection === 'cursos' }">
              <router-link class="nav-link" to="/Cursos" @click="setActiveSection('cursos')" custom v-slot="{ navigate }">
                <a @click="handleNavigation(navigate, 'cursos')" class="nav-link">
                  <span>Cursos</span>
                </a>
              </router-link>
            </li>
            <li class="nav-item" :class="{ active: activeSection === 'certificacoes' }">
              <router-link class="nav-link" to="/Certificacoes" @click="setActiveSection('certificacoes')" custom v-slot="{ navigate }">
                <a @click="handleNavigation(navigate, 'certificacoes')" class="nav-link">
                  <span>Certificações</span>
                </a>
              </router-link>
            </li>
            <li class="nav-item" :class="{ active: activeSection === 'contato' }">
              <router-link class="nav-link" to="/Contacto" @click="setActiveSection('contato')" custom v-slot="{ navigate }">
                <a @click="handleNavigation(navigate, 'contato')" class="nav-link">
                  <span>Contacto</span>
                </a>
              </router-link>
            </li>
            <li class="nav-item whatsapp-item">
              <a href="https://wa.me/+258846949523?text=Olá!%20Gostaria%20de%20saber%20mais%20sobre%20os%20vossos%20serviços%20e%20cursos%20de%20certificação.%20Podem%20me%20ajudar?" target="_blank" class="nav-link whatsapp-link" @click="closeMenu">
                <i class="bi bi-whatsapp"></i>
                <span>WhatsApp</span>
              </a>
            </li>
          </ul>
        </div>
        <div v-if="isMenuOpen" class="menu-overlay" @click="closeMenu"></div>
      </div>
    </nav>
</template>

<script>
export default {
  name: 'ProfessionalNavbar',
  data() {
    return {
      isMenuOpen: false,
      isScrolled: false,
      activeSection: 'inicio'
    }
  },
  watch: {
    '$route'() {
      this.updateActiveSection();
    }
  },
  methods: {
    toggleMenu() {
      this.isMenuOpen = !this.isMenuOpen;
    },
    closeMenu() {
      this.isMenuOpen = false;
      
      setTimeout(() => {
        this.isMenuOpen = false;
      }, 100);
    },
    setActiveSection(section) {
      this.activeSection = section;
      this.closeMenu();
    },
    handleNavigation(navigate, section) {
      this.setActiveSection(section);
      navigate();
    },
    handleScroll() {
      this.isScrolled = window.scrollY > 50
    },
    
    getInitialActiveSection() {
      const currentRoute = this.$route?.path || window.location.pathname;
      
      const routeMap = {
        '/': 'inicio',
        '/Depoimentos': 'depoimentos',
        '/Cursos': 'cursos', 
        '/Certificacoes': 'certificacoes',
        '/Contacto': 'contato',
        '/SobreNos': 'SobreNos',
        '/Ambiental': 'cursos',
        '/Qualidade': 'cursos',
        '/Saude': 'cursos',
        '/Higiene': 'cursos',
        '/Monitoria': 'cursos',
        '/Nebosh': 'cursos'
      };
      
      return routeMap[currentRoute] || 'inicio';
    },
    
    updateActiveSection() {
      const newActiveSection = this.getInitialActiveSection();
      this.activeSection = newActiveSection;
    }
  },
  
  mounted() {
    this.updateActiveSection();
    
    window.addEventListener('resize', () => {
      if (window.innerWidth > 768) {
        this.isMenuOpen = false;
      }
    });
    
    window.addEventListener('scroll', this.handleScroll);
    window.scrollTo(0, 0);
  },
  beforeUnmount() {
    window.removeEventListener('scroll', this.handleScroll);
  }
}
</script>

<style scoped>
.professional-navbar {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  background: rgba(255, 255, 255, 0.95);
  backdrop-filter: blur(20px);
  border-bottom: 1px solid rgba(0, 0, 0, 0.08);
  z-index: 9999;
  transition: all 0.3s ease;
  box-shadow: 0 2px 20px rgba(0, 0, 0, 0.1);
}

.navbar-container {
  max-width: 1400px;
  margin: 0 auto;
  padding: 0 2rem;
  display: flex;
  align-items: center;
  justify-content: space-between;
  height: 70px;
}

.navbar-brand {
  text-decoration: none;
  z-index: 10001;
  flex-shrink: 0;
}

.logo-container {
  display: flex;
  align-items: center;
  gap: 12px;
}

.logo-image {
  width: 180px;
  height: 90px;
  border-radius: 8px;
  object-fit: cover;
  transition: all 0.3s ease;
}

.logo-image:hover {
  transform: scale(1.05);
}

.brand-text {
  font-size: 1.8rem;
  font-weight: 700;
  letter-spacing: -0.5px;
}

.brand-primary {
  color: #2c3e50;
}

.brand-gradient {
  background: linear-gradient(45deg, #667eea, #764ba2);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.menu-toggle {
  display: none;
  flex-direction: column;
  background: none;
  border: none;
  cursor: pointer;
  padding: 10px;
  z-index: 10001;
  border-radius: 6px;
  transition: all 0.3s ease;
}

.menu-toggle:hover {
  background: rgba(102, 126, 234, 0.1);
}

.menu-toggle span {
  width: 25px;
  height: 3px;
  background: #2c3e50;
  margin: 3px 0;
  transition: all 0.3s ease;
  border-radius: 3px;
}

.menu-toggle.active span:nth-child(1) {
  transform: rotate(45deg) translate(5px, 5px);
}

.menu-toggle.active span:nth-child(2) {
  opacity: 0;
}

.menu-toggle.active span:nth-child(3) {
  transform: rotate(-45deg) translate(7px, -6px);
}

.nav-menu {
  display: flex;
  align-items: center;
  justify-content: flex-end;
  margin-left: auto;
  margin-right: 2rem;
}

.nav-links {
  display: flex;
  align-items: center;
  gap: 2rem;
  list-style: none;
  margin: 0;
  padding: 0;
}

.nav-item {
  position: relative;
}

.nav-link {
  display: flex;
  align-items: center;
  text-decoration: none;
  color: #2c3e50;
  font-weight: 600;
  font-size: 1rem;
  padding: 1rem 1.5rem;
  border-radius: 8px;
  transition: all 0.3s ease;
  position: relative;
  letter-spacing: 0.3px;
  cursor: pointer;
}

.nav-link::before {
  content: '';
  position: absolute;
  bottom: -5px;
  left: 50%;
  width: 0;
  height: 3px;
  background: linear-gradient(45deg, #667eea, #764ba2);
  transition: all 0.3s ease;
  transform: translateX(-50%);
  border-radius: 2px;
}

.nav-item.active .nav-link {
  color: #667eea !important;
  background: rgba(102, 126, 234, 0.1) !important;
}

.nav-item.active .nav-link::before {
  width: 60% !important;
}

.nav-item:not(.active) .nav-link:hover {
  color: #667eea;
  background: rgba(102, 126, 234, 0.05);
}

.nav-item:not(.active) .nav-link:hover::before {
  width: 60%;
}

.bi-whatsapp {
  font-size: 20px;
  margin-right: 8px;
  display: inline-block;
}

.whatsapp-link {
  color: #25D366 !important;
  background: rgba(37, 211, 102, 0.1);
  border: 2px solid rgba(37, 211, 102, 0.2);
}

.whatsapp-link:hover {
  color: #128C7E !important;
  background: rgba(37, 211, 102, 0.15);
  border-color: rgba(37, 211, 102, 0.3);
  transform: translateY(-1px) scale(1.02);
}

.whatsapp-link:hover .bi-whatsapp {
  transform: scale(1.1);
}

.menu-overlay {
  display: none;
}

.professional-navbar.scrolled {
  background: rgba(255, 255, 255, 0.98);
  box-shadow: 0 5px 30px rgba(0, 0, 0, 0.15);
}

.nav-item:hover .nav-link {
  transform: translateY(-1px);
}

.nav-link:focus {
  outline: 2px solid #667eea;
  outline-offset: 2px;
}

@media (max-width: 768px) {
  .professional-navbar {
    background: rgba(255, 255, 255, 0.98) !important;
    backdrop-filter: blur(10px);
    box-shadow: 0 2px 20px rgba(0, 0, 0, 0.15);
    border-bottom: 1px solid rgba(0, 0, 0, 0.1);
  }

  .navbar-container {
    padding: 0 1.5rem;
    height: 70px;
    position: relative;
  }

  .menu-toggle {
    display: flex;
    background: rgba(255, 255, 255, 0.9);
    border: 2px solid rgba(102, 126, 234, 0.2);
    box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
  }

  .menu-toggle:active {
    transform: scale(0.95);
  }

  .logo-image {
    width: 120px;
    height: 60px;
  }

  .nav-menu {
    position: fixed;
    top: 70px;
    right: -100%;
    width: 100%;
    height: 80vh;
    max-height: 600px;
    background: rgba(255, 255, 255, 0.98);
    backdrop-filter: blur(20px);
    flex-direction: column;
    justify-content: flex-start;
    align-items: center;
    padding: 3rem 1.5rem 2.5rem;
    transition: right 0.4s cubic-bezier(0.25, 0.46, 0.45, 0.94);
    margin-left: 0;
    margin-right: 0;
    box-shadow: -5px 0 30px rgba(0, 0, 0, 0.2);
    border-left: 1px solid rgba(102, 126, 234, 0.1);
    border-bottom: 1px solid rgba(102, 126, 234, 0.1);
    border-bottom-left-radius: 20px;
    overflow-y: auto;
    z-index: 10000;
  }

  .nav-menu.active {
    right: 0;
  }

  .menu-overlay {
    display: block;
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100vh;
    background: rgba(0, 0, 0, 0.3);
    z-index: 9999;
    opacity: 0;
    animation: fadeIn 0.3s ease forwards;
  }

  @keyframes fadeIn {
    to {
      opacity: 1;
    }
  }

  .nav-links {
    flex-direction: column;
    gap: 0;
    width: 100%;
    max-width: 320px;
    padding: 0;
    align-items: center;
    background: rgba(255, 255, 255, 0.95);
    border-radius: 0;
    overflow: hidden;
  }

  .nav-item {
    width: 100%;
    border-bottom: 1px solid rgba(102, 126, 234, 0.15);
  }

  .nav-item:last-child {
    border-bottom: none;
  }

  .nav-link {
    width: 100%;
    padding: 1.5rem 1.5rem;
    border-radius: 0;
    justify-content: center;
    color: #2c3e50;
    background: transparent;
    border: none;
    font-size: 1.2rem;
    font-weight: 600;
    letter-spacing: 0.3px;
    text-align: center;
    transform: translateY(30px);
    opacity: 0;
    transition: all 0.3s ease;
    box-shadow: none;
    min-height: 70px;
    max-height: 70px;
    display: flex;
    align-items: center;
    cursor: pointer;
    -webkit-tap-highlight-color: transparent;
    position: relative;
  }

  .nav-menu.active .nav-link {
    transform: translateY(0);
    opacity: 1;
  }

  .nav-link::before {
    display: none;
  }

  .nav-item.active .nav-link {
    background: rgba(102, 126, 234, 0.15) !important;
    color: #667eea !important;
  }

  .nav-item.active .nav-link::after {
    content: '';
    position: absolute;
    left: 0;
    top: 0;
    bottom: 0;
    width: 4px;
    background: #667eea;
  }

  .nav-item:not(.active):not(.whatsapp-item) .nav-link:hover,
  .nav-item:not(.active):not(.whatsapp-item) .nav-link:active {
    background: rgba(102, 126, 234, 0.1) !important;
    border-color: transparent !important;
    transform: translateY(0);
    box-shadow: none;
    color: #667eea !important;
  }

  .bi-whatsapp {
    font-size: 20px;
    margin-right: 8px;
    transition: transform 0.3s ease;
    display: inline-block;
  }

  .whatsapp-link {
    background: transparent !important;
    border-color: transparent !important;
    color: #25D366 !important;
  }

  .whatsapp-link:hover,
  .whatsapp-link:active {
    background: rgba(37, 211, 102, 0.1) !important;
    border-color: transparent !important;
    color: #128C7E !important;
    box-shadow: none;
  }

  .whatsapp-link:hover .bi-whatsapp {
    transform: scale(1.1);
  }

  .whatsapp-link.router-link-active::after {
    background: #25D366;
  }

  .nav-menu.active .nav-link:nth-child(1) { 
    transition-delay: 0.1s;
  }
  .nav-menu.active .nav-link:nth-child(2) { 
    transition-delay: 0.15s;
  }
  .nav-menu.active .nav-link:nth-child(3) { 
    transition-delay: 0.2s;
  }
  .nav-menu.active .nav-link:nth-child(4) { 
    transition-delay: 0.25s;
  }
  .nav-menu.active .nav-link:nth-child(5) { 
    transition-delay: 0.3s;
  }
  .nav-menu.active .nav-link:nth-child(6) { 
    transition-delay: 0.35s;
  }

  .nav-link:active {
    transform: scale(0.98) !important;
    transition: transform 0.1s ease;
  }
}

@media (max-width: 480px) {
  .navbar-container {
    height: 65px;
    padding: 0 1rem;
  }

  .logo-image {
    width: 100px;
    height: 50px;
  }

  .nav-menu {
    padding: 2.5rem 1rem 2rem;
    top: 65px;
    height: 75vh;
    max-height: 550px;
  }

  .nav-links {
    gap: 0;
    max-width: 320px;
  }

  .nav-link {
    font-size: 1.1rem;
    padding: 1.3rem 1.2rem;
    min-height: 65px;
    max-height: 65px;
  }
}

@media (hover: none) and (pointer: coarse) {
  .nav-link:hover {
    background: initial;
    transform: initial;
  }
  
  .nav-link:active {
    background: rgba(102, 126, 234, 0.1) !important;
    border-color: rgba(102, 126, 234, 0.4) !important;
    transform: scale(0.98);
  }
}
</style>