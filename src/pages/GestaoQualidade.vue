<template>
  <div class="iso-course-page">
    <section class="hero-section">
      <div class="container">
        <div class="row align-items-center">
          <div class="col-lg-6 order-lg-1 order-2">
            <div class="course-badge mb-3">
              <span class="badge bg-custom-blue text-white px-3 py-2 rounded-pill">
                <i class="bi bi-award me-2"></i>Gestão da Qualidade
              </span>
            </div>
            <h1 class="hero-title">ISO 9001 - Gestão da Qualidade</h1>
            <p class="hero-subtitle">
              Aprenda os princípios e requisitos do sistema de gestão da qualidade 
              mais reconhecido mundialmente
            </p>
            
            <div class="course-meta d-flex gap-4 mb-4">
              <div class="meta-item d-flex align-items-center">
                <i class="bi bi-clock text-custom-blue me-2"></i>
                <span>45 horas</span>
              </div>
              <div class="meta-item d-flex align-items-center">
                <i class="bi bi-people text-custom-blue me-2"></i>
                <span>Certificação ISO</span>
              </div>
              <div class="meta-item d-flex align-items-center">
                <i class="bi bi-trophy text-custom-blue me-2"></i>
                <span>Nível Executivo</span>
              </div>
            </div>

            <div class="hero-actions d-flex flex-column flex-md-row gap-3 align-items-start">
              <router-link to="/Contacto" class="btn btn-primary btn-lg px-4 py-3">
                <i class="bi bi-play-circle me-2"></i>Iniciar Curso
              </router-link>
              
              <div class="floating-card">
                <div class="card bg-white shadow p-3">
                  <div class="d-flex align-items-center">
                    <div class="icon-circle bg-custom-blue text-white me-3">
                      <i class="bi bi-check-lg"></i>
                    </div>
                    <div>
                      <h6 class="mb-0 fw-bold">Certificação Garantida</h6>
                      <small class="text-muted">95% de aprovação</small>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>

          <div class="col-lg-5 order-lg-2 order-1">
            <div class="hero-image">
              <img src="@/assets/imagens/image2.png" 
                   alt="ISO 9001" class="img-fluid rounded-4 shadow-lg">
            </div>
          </div>
        </div>
      </div>
    </section>

    <section class="py-5 bg-light">
      <div class="container">
        <div class="row">
          <div class="col-lg-12">
            <div class="course-content">
              <h2 class="section-title mb-4">Sobre o Curso</h2>
              <p class="lead mb-4">
                O curso ISO 9001 é ideal para profissionais que desejam dominar os princípios 
                da gestão da qualidade e implementar sistemas eficazes que garantam a satisfação 
                do cliente e melhoria contínua dos processos organizacionais.
              </p>

              <div class="course-modules mb-5">
                <h3 class="modules-title mb-4">Módulos do Curso</h3>
                <div class="accordion" id="moduleAccordion">
                  <!-- Módulo 1 -->
                  <div class="accordion-item border-0 shadow-sm mb-3">
                    <h2 class="accordion-header" id="heading1">
                      <button 
                        class="accordion-button" 
                        :class="{ 'collapsed': activeModule !== 1 }"
                        type="button" 
                        @click="toggleModule(1)"
                        :aria-expanded="activeModule === 1"
                        aria-controls="module1">
                        <div class="module-info">
                          <span class="module-number">01</span>
                          <div>
                            <h6 class="module-title mb-1">Fundamentos da Qualidade</h6>
                            <small class="text-muted">Princípios e conceitos básicos</small>
                          </div>
                        </div>
                      </button>
                    </h2>
                    <div 
                      id="module1" 
                      class="accordion-collapse collapse" 
                      :class="{ 'show': activeModule === 1 }"
                      aria-labelledby="heading1" 
                      data-bs-parent="#moduleAccordion">
                      <div class="accordion-body">
                        <ul class="list-unstyled">
                          <li class="mb-2"><i class="bi bi-check-circle text-custom-blue me-2"></i>História e evolução da ISO 9001</li>
                          <li class="mb-2"><i class="bi bi-check-circle text-custom-blue me-2"></i>Os 7 princípios da gestão da qualidade</li>
                          <li class="mb-2"><i class="bi bi-check-circle text-custom-blue me-2"></i>Estrutura da norma ISO 9001:2015</li>
                        </ul>
                      </div>
                    </div>
                  </div>

                  <!-- Módulo 2 -->
                  <div class="accordion-item border-0 shadow-sm mb-3">
                    <h2 class="accordion-header" id="heading2">
                      <button 
                        class="accordion-button collapsed" 
                        :class="{ 'collapsed': activeModule !== 2 }"
                        type="button" 
                        @click="toggleModule(2)"
                        :aria-expanded="activeModule === 2"
                        aria-controls="module2">
                        <div class="module-info">
                          <span class="module-number">02</span>
                          <div>
                            <h6 class="module-title mb-1">Sistema de Gestão da Qualidade</h6>
                            <small class="text-muted">Implementação e documentação</small>
                          </div>
                        </div>
                      </button>
                    </h2>
                    <div 
                      id="module2" 
                      class="accordion-collapse collapse" 
                      :class="{ 'show': activeModule === 2 }"
                      aria-labelledby="heading2" 
                      data-bs-parent="#moduleAccordion">
                      <div class="accordion-body">
                        <ul class="list-unstyled">
                          <li class="mb-2"><i class="bi bi-check-circle text-custom-blue me-2"></i>Mapeamento de processos</li>
                          <li class="mb-2"><i class="bi bi-check-circle text-custom-blue me-2"></i>Documentação do SGQ</li>
                          <li class="mb-2"><i class="bi bi-check-circle text-custom-blue me-2"></i>Política e objetivos da qualidade</li>
                        </ul>
                      </div>
                    </div>
                  </div>

                  <!-- Módulo 3 -->
                  <div class="accordion-item border-0 shadow-sm mb-3">
                    <h2 class="accordion-header" id="heading3">
                      <button 
                        class="accordion-button collapsed" 
                        :class="{ 'collapsed': activeModule !== 3 }"
                        type="button" 
                        @click="toggleModule(3)"
                        :aria-expanded="activeModule === 3"
                        aria-controls="module3">
                        <div class="module-info">
                          <span class="module-number">03</span>
                          <div>
                            <h6 class="module-title mb-1">Controle de Processos</h6>
                            <small class="text-muted">Monitoramento e medição</small>
                          </div>
                        </div>
                      </button>
                    </h2>
                    <div 
                      id="module3" 
                      class="accordion-collapse collapse" 
                      :class="{ 'show': activeModule === 3 }"
                      aria-labelledby="heading3" 
                      data-bs-parent="#moduleAccordion">
                      <div class="accordion-body">
                        <ul class="list-unstyled">
                          <li class="mb-2"><i class="bi bi-check-circle text-custom-blue me-2"></i>Controle de documentos</li>
                          <li class="mb-2"><i class="bi bi-check-circle text-custom-blue me-2"></i>Gestão de recursos</li>
                          <li class="mb-2"><i class="bi bi-check-circle text-custom-blue me-2"></i>Realização do produto/serviço</li>
                        </ul>
                      </div>
                    </div>
                  </div>

                  <!-- Módulo 4 -->
                  <div class="accordion-item border-0 shadow-sm">
                    <h2 class="accordion-header" id="heading4">
                      <button 
                        class="accordion-button collapsed" 
                        :class="{ 'collapsed': activeModule !== 4 }"
                        type="button" 
                        @click="toggleModule(4)"
                        :aria-expanded="activeModule === 4"
                        aria-controls="module4">
                        <div class="module-info">
                          <span class="module-number">04</span>
                          <div>
                            <h6 class="module-title mb-1">Avaliação e Melhoria</h6>
                            <small class="text-muted">Auditoria e melhoria contínua</small>
                          </div>
                        </div>
                      </button>
                    </h2>
                    <div 
                      id="module4" 
                      class="accordion-collapse collapse" 
                      :class="{ 'show': activeModule === 4 }"
                      aria-labelledby="heading4" 
                      data-bs-parent="#moduleAccordion">
                      <div class="accordion-body">
                        <ul class="list-unstyled">
                          <li class="mb-2"><i class="bi bi-check-circle text-custom-blue me-2"></i>Satisfação do cliente</li>
                          <li class="mb-2"><i class="bi bi-check-circle text-custom-blue me-2"></i>Auditorias internas</li>
                          <li class="mb-2"><i class="bi bi-check-circle text-custom-blue me-2"></i>Ações corretivas e preventivas</li>
                        </ul>
                      </div>
                    </div>
                  </div>
                </div>
              </div>

              <div class="course-benefits">
                <h3 class="benefits-title mb-4">O que você vai aprender</h3>
                <div class="row g-4">
                  <div class="col-md-6">
                    <div class="benefit-item d-flex">
                      <div class="benefit-icon">
                        <i class="bi bi-gear-wide-connected"></i>
                      </div>
                      <div>
                        <h6 class="benefit-title fw-bold">Gestão de Processos</h6>
                        <p class="text-muted mb-0">Domine técnicas de mapeamento e otimização de processos</p>
                      </div>
                    </div>
                  </div>
                  <div class="col-md-6">
                    <div class="benefit-item d-flex">
                      <div class="benefit-icon">
                        <i class="bi bi-person-check"></i>
                      </div>
                      <div>
                        <h6 class="benefit-title fw-bold">Satisfação do Cliente</h6>
                        <p class="text-muted mb-0">Aprenda a medir e melhorar a satisfação dos clientes</p>
                      </div>
                    </div>
                  </div>
                  <div class="col-md-6">
                    <div class="benefit-item d-flex">
                      <div class="benefit-icon">
                        <i class="bi bi-clipboard-check"></i>
                      </div>
                      <div>
                        <h6 class="benefit-title fw-bold">Auditoria Interna</h6>
                        <p class="text-muted mb-0">Desenvolva habilidades para conduzir auditorias eficazes</p>
                      </div>
                    </div>
                  </div>
                  <div class="col-md-6">
                    <div class="benefit-item d-flex">
                      <div class="benefit-icon">
                        <i class="bi bi-arrow-up-circle"></i>
                      </div>
                      <div>
                        <h6 class="benefit-title fw-bold">Melhoria Contínua</h6>
                        <p class="text-muted mb-0">Implemente ciclos de melhoria contínua na organização</p>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  name: 'ISO9001CoursePage',
  data() {
    return {
      activeModule: 1 // Módulo 1 aberto por padrão
    }
  },
  methods: {
    toggleModule(moduleNumber) {
      // Se o módulo clicado já está ativo, fecha ele
      if (this.activeModule === moduleNumber) {
        this.activeModule = null;
      } else {
        // Caso contrário, abre o módulo clicado
        this.activeModule = moduleNumber;
      }
    }
  }
}
</script>

<style scoped>
/* Cores customizadas */
.bg-custom-blue {
  background-color: #3d4ed8 !important;
}

.text-custom-blue {
  color: #3d4ed8 !important;
}

.iso-course-page {

}

.hero-section {
  background: linear-gradient(135deg, #f8faff 0%, #f0f4ff 100%);
  padding: 10rem 0;
  position: relative;
}

.hero-title {
  font-size: 3.5rem;
  font-weight: 800;
  color: #3d4ed8;
  margin-bottom: 1.5rem;
  line-height: 1.2;
}

.hero-subtitle {
  font-size: 1.3rem;
  color: #6b7280;
  margin-bottom: 2rem;
  line-height: 1.6;
}

.course-meta {
  border-left: 4px solid #3d4ed8;
  padding-left: 1rem;
  margin-bottom: 2rem;
}

.meta-item {
  font-weight: 500;
  color: #4b5563;
}

.hero-actions .btn {
  font-weight: 600;
  border-radius: 50px;
}

.btn-primary {
  background: linear-gradient(135deg, #3d4ed8, #2d3ba8);
  border: none;
}

.btn-primary:hover {
  background: linear-gradient(135deg, #2d3ba8, #1e2871);
  transform: translateY(-2px);
}

.hero-image {
  position: relative;
}

.floating-card {
  position: relative;
  animation: float 3s ease-in-out infinite;
}

.floating-card .card {
  border: none;
  border-radius: 15px;
}

@keyframes float {
  0%, 100% { transform: translateY(0px); }
  50% { transform: translateY(-10px); }
}

.icon-circle {
  width: 50px;
  height: 50px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
}

.section-title {
  color: #3d4ed8;
  font-weight: 700;
  font-size: 2.5rem;
  text-align: center;
}

.modules-title {
  color: #2c3e50;
  font-weight: 600;
  font-size: 2rem;
  text-align: center;
}

.benefits-title {
  color: #2c3e50;
  font-weight: 600;
  font-size: 2rem;
  text-align: center;
}

.module-title {
  font-size: 1rem;
  font-weight: 600;
  color: #2c3e50;
}

.benefit-title {
  font-size: 1.1rem;
  color: #2c3e50;
}


.course-modules .accordion-button {
  background: white;
  border: none;
  box-shadow: none;
  padding: 1.5rem;
  position: relative;
}

.course-modules .accordion-button:not(.collapsed) {
  background: white;
  color: #3d4ed8;
  box-shadow: none;
}

.course-modules .accordion-button:focus {
  box-shadow: 0 0 0 0.25rem rgba(61, 78, 216, 0.25);
  border: none;
}

.module-info {
  display: flex;
  align-items: center;
  gap: 1rem;
  flex: 1;
}

.module-number {
  background: linear-gradient(135deg, #3d4ed8, #2d3ba8);
  color: white;
  width: 40px;
  height: 40px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: 700;
}


.accordion-collapse {
  transition: all 0.3s ease;
}

.benefit-item {
  gap: 1rem;
  margin-bottom: 1.5rem;
}

.benefit-icon {
  width: 50px;
  height: 50px;
  background: rgba(61, 78, 216, 0.1);
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #3d4ed8;
  font-size: 1.5rem;
  flex-shrink: 0;
}

@media (max-width: 768px) {
  .hero-section {
    padding: 6rem 0 4rem;
  }

  .hero-title {
    font-size: 2.2rem;
    line-height: 1.3;
    text-align: center;
    margin-bottom: 1.2rem;
  }
  
  .hero-subtitle {
    font-size: 1.1rem;
    margin-bottom: 1.8rem;
    text-align: center;
    line-height: 1.5;
  }

  .section-title {
    font-size: 2rem;
    margin-bottom: 2rem;
    text-align: center;
  }

  .modules-title {
    font-size: 1.6rem;
    margin-bottom: 2rem;
    text-align: center;
  }

  .benefits-title {
    font-size: 1.6rem;
    margin-bottom: 2rem;
    text-align: center;
  }

  .module-title {
    font-size: 0.95rem;
    line-height: 1.3;
  }

  .benefit-title {
    font-size: 1rem;
    line-height: 1.3;
  }

  .course-meta {
    flex-direction: column;
    gap: 1rem !important;
    border-left: none;
    border-top: 4px solid #3d4ed8;
    padding-left: 0;
    padding-top: 1rem;
    text-align: center;
  }

  .meta-item {
    justify-content: center;
    text-align: center;
  }
  
  .hero-actions {
    flex-direction: column !important;
    align-items: stretch !important;
    gap: 1rem !important;
  }

  .hero-actions .btn {
    width: 100%;
    padding: 1rem;
    font-size: 1.1rem;
  }
  
  .floating-card {
    margin-top: 1rem;
    width: 100%;
  }

  .floating-card .card {
    text-align: center;
  }

  .course-badge {
    text-align: center;
  }

  .col-lg-6:first-child {
    margin-bottom: 0;
  }

  .col-lg-5 {
    margin-bottom: 3rem;
  }

  .hero-image {
    text-align: center;
  }

  .hero-image img {
    max-width: 90%;
    height: auto;
  }

  .lead {
    text-align: center;
    font-size: 1rem;
    line-height: 1.6;
  }
}

@media (max-width: 576px) {
  .hero-section {
    padding: 5rem 0 3rem;
  }

  .hero-title {
    font-size: 1.8rem;
    line-height: 1.3;
    margin-bottom: 1rem;
  }

  .hero-subtitle {
    font-size: 1rem;
    margin-bottom: 1.5rem;
    line-height: 1.4;
  }

  .section-title {
    font-size: 1.7rem;
    margin-bottom: 1.5rem;
    line-height: 1.2;
  }

  .modules-title {
    font-size: 1.4rem;
    margin-bottom: 1.5rem;
    line-height: 1.3;
  }

  .benefits-title {
    font-size: 1.4rem;
    margin-bottom: 1.5rem;
    line-height: 1.3;
  }

  .module-title {
    font-size: 0.9rem;
    line-height: 1.2;
  }

  .benefit-title {
    font-size: 0.95rem;
    line-height: 1.2;
  }

  .course-meta {
    gap: 0.8rem !important;
    margin-bottom: 1.5rem;
  }

  .meta-item {
    font-size: 0.9rem;
  }

  .meta-item i {
    font-size: 1rem;
  }

  .hero-actions .btn {
    padding: 0.9rem;
    font-size: 1rem;
  }

  .floating-card .card {
    padding: 1rem !important;
  }

  .floating-card .icon-circle {
    width: 40px;
    height: 40px;
  }

  .floating-card h6 {
    font-size: 0.9rem;
  }

  .floating-card small {
    font-size: 0.8rem;
  }

  .container {
    padding-left: 1rem;
    padding-right: 1rem;
  }

  .lead {
    font-size: 0.95rem;
    line-height: 1.5;
    margin-bottom: 2rem;
  }

  .accordion-button {
    padding: 1rem !important;
  }

  .module-info {
    gap: 0.8rem;
  }

  .module-number {
    width: 35px;
    height: 35px;
    font-size: 0.9rem;
  }

  .benefit-item {
    gap: 0.8rem;
    margin-bottom: 1.2rem;
  }

  .benefit-icon {
    width: 45px;
    height: 45px;
    font-size: 1.3rem;
  }
}

@media (max-width: 480px) {
  .hero-section {
    padding: 4rem 0 2rem;
  }

  .hero-title {
    font-size: 1.6rem;
    line-height: 1.2;
  }

  .hero-subtitle {
    font-size: 0.95rem;
  }

  .section-title {
    font-size: 1.5rem;
    line-height: 1.1;
  }

  .modules-title, .benefits-title {
    font-size: 1.3rem;
    line-height: 1.2;
  }

  .module-title {
    font-size: 0.85rem;
  }

  .benefit-title {
    font-size: 0.9rem;
  }

  .lead {
    font-size: 0.9rem;
  }
}
</style>