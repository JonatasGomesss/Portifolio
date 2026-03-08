<template>
  <v-container class="pa-0" fluid>
    <header class="header">
      <ul class="list">
        <li>Abilidades De Tecnologia</li>
        <li>Projetos</li>
      </ul>
    </header>
    <v-container class="post" fluid>
      <section class="apresentacao">
        <v-row
          align="center"
          class="apresentacao-row"
          justify="space-between"
          no-gutters
        >
          <v-col class="apresentacao-texto" cols="12" md="6">
            <span class="apresentacao-badge">Olá, eu sou</span>

            <h1 class="apresentacao-nome">
              <span class="tag">&lt;</span>
              Jonatas
              <span class="tag">/&gt;</span>
            </h1>
            <p class="apresentacao-cargo">
              Desenvolvedor <span class="cargo-destaque">Front-End</span>
            </p>
            <p class="apresentacao-descricao">
              Sou desenvolvedor Front-End focado em criar interfaces modernas,
              responsivas e bem estruturadas. Gosto de transformar ideias em
              experiências digitais funcionais utilizando JavaScript, Vue.js,
              HTML e CSS.
            </p>

            <p class="apresentacao-descricao">
              Busco sempre escrever código limpo, seguir boas práticas e
              desenvolver aplicações que unam performance, organização e ótima
              experiência para o usuário.
            </p>

            <div class="apresentacao-cta">
              <v-btn
                class="btn-primary"
                size="large"
                variant="flat"
                @click.prevent="scrollToProjetos"
              >Meus Projetos
                Ver Projetos
              </v-btn>

              <v-btn
                class="btn-outline"
                size="large"
                variant="outlined"
                @click="openContato"
              >
                Contato
              </v-btn>
            </div>
          </v-col>
          <v-col class="apresentacao-visual" cols="12" md="6">
            <div class="hero-visual">
              <div class="code-window">
                <div class="code-header">
                  <span class="code-dot" />
                  <span class="code-dot" />
                  <span class="code-dot" />
                  <span class="code-title"> portfolio.vue </span>
                </div>

                <div class="code-body">
                  <pre><code><span class="code-keyword">const</span> <span class="code-var">dev</span> = {
  <span class="code-prop">nome</span>: <span class="code-string">'Jonatas'</span>,
  <span class="code-prop">stack</span>: [<span class="code-string">'Vue'</span>, <span class="code-string">'JS'</span>, <span class="code-string">'CSS'</span>],
  <span class="code-prop">foco</span>: <span class="code-string">'Front-End'</span>
};</code></pre>
                </div>
              </div>
              <div class="tech-float">
                <v-icon class="tech-icon tech-vue" size="44">
                  mdi-vuejs
                </v-icon>

                <v-icon class="tech-icon tech-js" size="40">
                  mdi-language-javascript
                </v-icon>

                <v-icon class="tech-icon tech-html" size="38">
                  mdi-language-html5
                </v-icon>

                <v-icon class="tech-icon tech-css" size="38">
                  mdi-language-css3
                </v-icon>
              </div>
            </div>
          </v-col>
        </v-row>
      </section>
      <v-divider
        color="primary"
        style="max-width: 400px; margin: auto"
        thickness="3"
      />
      <div
        style="
          display: flex;
          justify-content: center;
          align-items: center;
          margin-top: 5%;
          margin-bottom: 5%;
        "
      >
        <div class="titulo-tech">
          <h2>Principais Tecnologias</h2>
          <p>
            Principais ferramentas e tecnologias que utilizo para construir
            minhas interfaces
          </p>
        </div>
      </div>

      <v-container class="skills">
        <v-row class="align-center justify-center">
          <v-col cols="12" md="6">
            <v-card
              class="mx-auto"
              style="border-left: 5px solid #42b883"
              title="Vue.js"
            >
              <v-card-text class="ma-2">
                Vue.js é o framework que escolhi para desenvolver interfaces
                modernas e reativas.
              </v-card-text>
            </v-card>
          </v-col>

          <v-col cols="12" md="6">
            <v-card
              class="mx-auto"
              prepend-icon="mdi-language-html5"
              style="border-left: 5px solid #e34c26"
              title="HTML"
            >
              <v-card-text class="ma-2">
                HTML é a linguagem responsável por estruturar todo o conteúdo
                das páginas web.
              </v-card-text>
            </v-card>
          </v-col>

          <v-col cols="12" md="6">
            <v-card
              class="mx-auto"
              prepend-icon="mdi-language-css3"
              style="border-left: 5px solid #264de4"
              title="CSS"
            >
              <v-card-text class="ma-2">
                CSS é usado para estilizar e organizar o layout das páginas,
                criando interfaces visuais.
              </v-card-text>
            </v-card>
          </v-col>

          <v-col cols="12" md="6">
            <v-card
              class="mx-auto"
              prepend-icon="mdi-language-javascript"
              style="border-left: 5px solid #f7df1e"
              title="JavaScript"
            >
              <v-card-text class="ma-2">
                JavaScript é a linguagem responsável pela lógica e
                interatividade das aplicações web.
              </v-card-text>
            </v-card>
          </v-col>
        </v-row>
      </v-container>

      <v-container id="projetos">
        <div class="projetos-container">
          <div class="infoProjetos">
            <h1>Meus Projetos</h1>
            <p>
              Projetos focados na construção de interfaces modernas e
              funcionais, aplicando na prática tecnologias de front-end e boas
              práticas de design.
            </p>
          </div>
        </div>
      </v-container>

      <v-container id="projetos" class="mt-10 pa-5" fluid>
        <v-row class="tecnologias">
          <v-col cols="12" md="5">
            <v-card class="project-card mx-auto" width="100%">
              <v-hover v-slot="{ isHovering, props }">
                <v-img
                  v-bind="props"
                  class="project-img"
                  cover
                  height="250"
                  src="../assets/tela-login-beryl.vercel.app_.png"
                >
                  <v-expand-transition>
                    <div
                      v-if="isHovering"
                      class="overlay d-flex flex-column align-center justify-center"
                    >
                      <v-btn
                        class="ma-2"
                        color="white"
                        href="https://tela-login-beryl.vercel.app/"
                        target="_blank"
                        variant="outlined"
                      >
                        Ver Projeto
                      </v-btn>
                    </div>
                  </v-expand-transition>
                </v-img>
              </v-hover>

              <v-card-title class="text-h6"> Tela de Login </v-card-title>

              <v-card-text style="width:100%; padding: 0;">
                <div class="techs">
                  <v-chip color="green" size="default">Vue</v-chip>
                  <v-chip color="blue" size="default">Vuetify</v-chip>
                  <v-chip color="yellow" size="default">JavaScript</v-chip>
                </div>
              </v-card-text>
            </v-card>
          </v-col>

          <v-col cols="12" md="5">
            <v-card class="project-card mx-auto" width="100%">
              <v-hover v-slot="{ isHovering, props }">
                <v-img
                  v-bind="props"
                  class="project-img"
                  cover
                  height="250"
                  src="../assets/filmes-series-psi.vercel.app_.png"
                >
                  <v-expand-transition>
                    <div
                      v-if="isHovering"
                      class="overlay d-flex flex-column align-center justify-center"
                    >
                      <v-btn
                        class="ma-2"
                        color="white"
                        href="https://filmes-series-psi.vercel.app/"
                        target="_blank"
                        variant="outlined"
                      >
                        Ver Projeto
                      </v-btn>
                    </div>
                  </v-expand-transition>
                </v-img>
              </v-hover>

              <v-card-title class="text-h6"> Filmes e Series </v-card-title>

              <v-card-text style="width:100%; padding: 0;">
                <div class="techs">
                  <v-chip color="green" size="default">Vue</v-chip>
                  <v-chip color="blue" size="default">Vuetify</v-chip>
                  <v-chip color="purple" size="default">API</v-chip>
                  <v-chip color="yellow" size="default">JavaScript</v-chip>
                </div>
              </v-card-text>
            </v-card>
          </v-col>

          <v-col cols="12" md="5">
            <v-card class="project-card mx-auto" width="100%">
              <v-hover v-slot="{ isHovering, props }">
                <v-img
                  v-bind="props"
                  class="project-img"
                  cover
                  height="250"
                  src="../assets/viagem-de-chihiro-theta.vercel.app_.png"
                >
                  <v-expand-transition>
                    <div
                      v-if="isHovering"
                      class="overlay d-flex flex-column align-center justify-center"
                    >
                      <v-btn
                        class="ma-2"
                        color="white"
                        href="https://viagem-de-chihiro-theta.vercel.app/"
                        target="_blank"
                        variant="outlined"
                      >
                        Ver Projeto
                      </v-btn>
                    </div>
                  </v-expand-transition>
                </v-img>
              </v-hover>

              <v-card-title class="text-h6"> Viagem de Chihiro </v-card-title>

              <v-card-text style="width:100%; padding: 0;">
                <div class="techs">
                  <v-chip color="red" size="default">Html</v-chip>
                  <v-chip color="blue" size="default">Css</v-chip>
                </div>
              </v-card-text>
            </v-card>
          </v-col>
          <v-col cols="12" md="5">
            <v-card class="project-card mx-auto" width="100%">
              <v-hover v-slot="{ isHovering, props }">
                <v-img
                  v-bind="props"
                  class="project-img"
                  cover
                  height="250"
                  src="../assets/viagem-de-chihiro-theta.vercel.app_.png"
                >
                  <v-expand-transition>
                    <div
                      v-if="isHovering"
                      class="overlay d-flex flex-column align-center justify-center"
                    >
                      <v-btn
                        class="ma-2"
                        color="white"
                        href="https://viagem-de-chihiro-theta.vercel.app/"
                        target="_blank"
                        variant="outlined"
                      >
                        Ver Projeto
                      </v-btn>
                    </div>
                  </v-expand-transition>
                </v-img>
              </v-hover>

              <v-card-title class="text-h6"> Viagem de Chihiro </v-card-title>

              <v-card-text style="width:100%; padding: 0;">
                <div class="techs">
                  <v-chip color="red" size="default">Html</v-chip>
                  <v-chip color="blue" size="default">Css</v-chip>
                </div>
              </v-card-text>
            </v-card>
          </v-col>
        </v-row>
      </v-container>

      <v-navigation-drawer
        v-model="contatoDrawer"
        class="contato-drawer"
        location="right"
        temporary
        width="340"
      >
        <v-sheet class="contato-sheet pa-4" elevation="0">
          <h3 class="contato-title">Meus Contatos</h3>
          <p class="contato-subtitle">
            Fale comigo pelos canais abaixo:
          </p>

          <v-list density="comfortable" nav>
            <v-list-item
              href="mailto:jonatasgomes1090@gmail.com?subject=Contato pelo Portfólio"
              link
              prepend-icon="mdi-email-outline"
            >
              <v-list-item-title>E-mail</v-list-item-title>
            </v-list-item>

            <v-list-item
              href="tel:+5588996473623"
              link
              prepend-icon="mdi-phone-outline"
            >
              <v-list-item-title>Telefone</v-list-item-title>
            </v-list-item>
            <v-list-item
              href="https://www.linkedin.com/in/jonatasgomess/"
              prepend-icon="mdi-linkedin"
              target="_blank"
            >
              <v-list-item-title>LinkedIn</v-list-item-title>
            </v-list-item>

            <v-list-item
              href="https://github.com/JonatasGomesss"
              prepend-icon="mdi-github"
              target="_blank"
            >
              <v-list-item-title>GitHub</v-list-item-title>
            </v-list-item>
          </v-list>
        </v-sheet>
      </v-navigation-drawer>
    </v-container>
  </v-container>
</template>
<script setup>
  import { ref } from 'vue'

  const contatoDrawer = ref(false)

  function scrollToProjetos () {
    const section = document.querySelector('#projetos')
    if (section) {
      section.scrollIntoView({ behavior: 'smooth', block: 'start' })
    }
  }

  function openContato () {
    contatoDrawer.value = true
  }
</script>

<style>
.apresentacao-nome {
  font-size: clamp(2.5rem, 6vw, 3.5rem);
  font-weight: 800;
  letter-spacing: -0.02em;
  color: white;
  font-family: "Fira Code", monospace;
}

.apresentacao-nome .tag {
  color: #42b883; /* cor estilo dev / vue */
  font-weight: 600;
}
.text-h6 {
  position: relative;
}

.text-h6::before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 2px;

  background: rgb(10, 140, 105);

  box-shadow:
    0 0 6px rgba(8, 101, 76, 0.8),
    0 0 12px rgba(8, 101, 76, 0.6),
    0 0 20px rgba(8, 101, 76, 0.4);
}
.titulo-tech {
  text-align: center;
  margin: 10px 0 10px;
}

.titulo-tech h2 {
  font-size: 2.3rem;
  font-weight: 700;
  color: #fff;
  position: relative;
  display: inline-block;
  margin-bottom: 12px;
}

.titulo-tech h2::after {
  content: "";
  position: absolute;
  left: 50%;
  bottom: -8px;
  transform: translateX(-50%);
  width: 60px;
  height: 3px;
  background: linear-gradient(90deg, #00d4aa, #00ffff);
  border-radius: 2px;
}

.titulo-tech p {
  color: #9ca3af;
  font-size: 0.95rem;
}

.contato-title {
  font-size: 1.25rem;
  font-weight: 600;
  margin-bottom: 8px;
  color: #e5e7eb;
}

.contato-subtitle {
  font-size: 0.95rem;
  color: #9ca3af;
  margin-bottom: 16px;
}

.contato-drawer {
  background: transparent !important;
  border-left: 1px solid rgba(148, 163, 184, 0.35);
  box-shadow:
    0 18px 45px rgba(0, 0, 0, 0.75),
    0 0 35px rgba(34, 211, 238, 0.22);
  backdrop-filter: blur(18px);
}

.contato-sheet {
  height: 100%;
  background: radial-gradient(
      circle at top left,
      rgba(0, 212, 170, 0.16),
      transparent 55%
    )
    #050816;
  color: #e5e7eb;
  display: flex;
  flex-direction: column;
  gap: 8px;
}

.contato-drawer .v-list {
  margin-top: 8px;
}

.contato-drawer .v-list-item {
  border-radius: 10px;
  transition:
    background-color 0.2s ease,
    transform 0.15s ease;
}

.contato-drawer .v-list-item:hover {
  background-color: rgba(15, 23, 42, 0.85);
  transform: translateX(2px);
}

.contato-drawer .v-list-item-title {
  font-weight: 500;
}

.contato-drawer .v-icon {
  color: #22d3ee !important;
}
.projetos-container {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 80px 20px;
  position: relative;
}

.infoProjetos {
  width: 100%;
  text-align: center;
  background: radial-gradient(
      circle at top left,
      rgba(0, 212, 170, 0.16),
      transparent 55%
    )
    #050816;
  border-radius: 16px;
  border: 1px solid rgba(148, 163, 184, 0.35);
  box-shadow:
    0 18px 45px rgba(0, 0, 0, 0.75),
    0 0 35px rgba(34, 211, 238, 0.22);
  backdrop-filter: blur(14px);
}

.infoProjetos h1 {
  font-size: 2.2rem;
  margin-bottom: 15px;
  color: #fff;
  font-weight: 700;
  letter-spacing: -0.02em;
  position: relative;
}

.infoProjetos h1::after {
  content: "";
  position: absolute;
  left: 50%;
  transform: translateX(-50%);
  bottom:-25%;
  width: 80px;
  height: 3px;
  background: linear-gradient(90deg, #6366f1, #22d3ee);
  border-radius: 999px;
}

.infoProjetos p {
  font-size: 1.06rem;
  padding: 3% 0% 3% 0%;
  color: #92b7ab;
  max-width: 550px;
  margin: auto;
}

.skills {
  padding: 70px 16px 90px;
}

.skills .v-row {
  row-gap: 24px;
}

.skills .v-card {
  background: transparent !important;
  border-radius: 12px;
  border: 1px solid rgba(148, 163, 184, 0.5);
  box-shadow: none;
  transition:
    transform 0.2s ease,
    border-color 0.2s ease,
    background-color 0.2s ease;
}

.skills .v-card:hover {
  transform: translateY(-2px);
  border-color: rgba(56, 189, 248, 0.7);
  background-color: rgba(15, 23, 42, 0.6);
}

.skills .v-card-title {
  font-weight: 600;
  letter-spacing: 0.03em;
}

.skills .v-card-text {
  color: #cbd5f5;
}

.skills .v-chip {
  font-weight: 500;
  text-transform: none;
}

@media (max-width: 960px) {
  .projetos-container {
    padding: 60px 18px;
  }
  .infoProjetos {
    padding: 32px 24px;
  }
}
.project-card {
  border-radius: 10px;
  overflow: hidden;
  cursor: pointer;
  background: radial-gradient(
    circle at top left,
    rgba(34, 211, 238, 0.12),
    rgba(15, 23, 42, 0.96)
  );
  border: 1px solid rgba(148, 163, 184, 0.45);
  box-shadow: 0 18px 45px rgba(15, 23, 42, 0.9);
  transition:
    transform 0.28s ease,
    box-shadow 0.28s ease,
    border-color 0.28s ease,
    background-color 0.28s ease;
}

.project-card:hover {
  transform: translateY(-6px);
  border-color: rgba(56, 189, 248, 0.8);
  box-shadow:
    0 24px 60px rgba(15, 23, 42, 0.95),
    0 0 40px rgba(56, 189, 248, 0.28);
}

.project-img {
  flex-shrink: 0;
}

.project-img img {
  transition: transform 0.4s ease;
}

.project-card:hover .project-img img {
  transform: scale(1.04);
}

.overlay {
  background: linear-gradient(
    180deg,
    rgba(15, 23, 42, 0.05),
    rgba(15, 23, 42, 0.92)
  );
  height: 100%;
  width: 100%;
}

.techs {
  justify-content: center;
  width: 100%;
  display: flex;
  gap: 6px;
  flex-wrap: wrap;
}

.project-card .v-card-title {
  font-weight: 600;
  letter-spacing: -0.01em;
  padding-top: 14px;
  padding-bottom: 4px;
  white-space: normal;
  overflow: visible;
  text-overflow: unset;
}

.project-card .v-chip {
  font-weight: 500;
  text-transform: none;
  border-radius: 999px;
}

.tecnologias .v-col {
  display: flex;
  align-items: stretch;
}

.project-card {
  height: 100%;
  min-height: 380px;
  display: flex;
  flex-direction: column;
  flex: 1 1 auto;
}

.mx-auto {
  transition: transform 0.3s ease;
}

.btnLink:hover {
  transform: scale(1.1);
}
.btnLink {
  margin: auto;
  transition: transform 0.2s ease;
  width: 150px;
  border: #00ffff 1px solid;
}
.tecnologias {
  padding: 60px 16px 90px;
  justify-content: center;
  gap: 24px;
  border: none;
}
.header {
  box-shadow: 0px 1px 17px rgba(133, 132, 132, 0.5);
  display: flex;
  width: 100%;
  align-items: center;
  justify-content: space-between;
}

.list {
  display: flex;
  gap: 26px;
  font-size: 22px;
  list-style: none;
  font-weight: 400;
}
.list li {
  position: relative;
  cursor: pointer;
}

.list li::after {
  content: "";
  position: absolute;
  left: 0;
  bottom: -4px;
  width: 0;
  height: 2px;
  background-color: #00ffff;
  box-shadow:
    0 0 5px #068a8a,
    0 0 10px #068a8a,
    0 0 20px #068a8a;
  transition: width 0.2s ease;
}
.list li:hover::after {
  width: 100%;
}
.apresentacao {
  margin: 4% 0 5%;
  padding: 3rem 1.5rem;
  width: 100%;
  gap: 2rem;
  min-height: 420px;
  position: relative;
  overflow: hidden;
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
}

.apresentacao-row {
  max-width: 1200px;
  margin: 0 auto;
}

.apresentacao-badge {
  display: inline-block;
  font-size: 0.9rem;
  font-weight: 500;
  letter-spacing: 0.15em;
  text-transform: uppercase;
  color: #00d4aa;
  margin-bottom: 0.5rem;
  padding: 0.25rem 0.75rem;
  background: rgba(0, 212, 170, 0.12);
  border-radius: 20px;
  border: 2px solid #00d4aa40;
}

.apresentacao-nome {
  font-weight: 400;
  color: #fff;
  margin: 0 0 0.25rem 0;
  letter-spacing: -0.02em;
  line-height: 1.1;
  position: relative;
  margin-bottom: 1.5rem;
}

.apresentacao-nome::after {
  content: "";
  position: absolute;
  left: 0;
  bottom: -6px;
  width: 60px;
  height: 3px;
  background: linear-gradient(90deg, #6366f1, #22d3ee);
  border-radius: 2px;
}

.apresentacao-cargo {
  font-size: clamp(2.40rem, 2vw, 1.6rem);
  color: #cfcfcf;
  font-weight: 500;
  letter-spacing: 0.03em;
}

.cargo-destaque {
  color: #42b883;
  font-weight: 700;
  position: relative;
}

.cargo-destaque::after {
  content: "";
  position: absolute;
  left: 0;
  bottom: -3px;
  width: 100%;
  height: 2px;
  background: #42b883;
  border-radius: 2px;
}
@media (max-width: 960px) {
  .apresentacao {
    display: flex;
    flex-direction: column-reverse;
    align-items: center;
    justify-content: center;
    color: #ffffff;
  }
}
.cargo-destaque {
  background: linear-gradient(135deg, #00d4aa, #00ffff);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  font-weight: 700;
}

.apresentacao-descricao {
  font-size: 1rem;
  line-height: 1.7;
  color: #a0a0a0;
  max-width: 32rem;
  margin: 0 0 0.75rem 0;
}

.apresentacao-cta {
  display: flex;
  gap: 1rem;
  margin-top: 1.5rem;
  flex-wrap: wrap;
}

.apresentacao-cta .btn-primary {
  background: linear-gradient(135deg, #00a88a, #00d4aa) !important;
  color: #fff !important;
  font-weight: 600;
  border-radius: 12px;
  text-transform: none;
  box-shadow: 0 4px 20px rgba(0, 212, 170, 0.35);
  transition:
    transform 0.2s,
    box-shadow 0.2s;
}

.apresentacao-cta .btn-primary:hover {
  transform: translateY(-2px);
  box-shadow: 0 6px 28px rgba(0, 212, 170, 0.45);
}

.apresentacao-cta .btn-outline {
  border: 2px solid rgba(0, 255, 255, 0.5) !important;
  color: #00ffff !important;
  border-radius: 12px;
  text-transform: none;
  font-weight: 600;
  transition: all 0.2s;
}

.apresentacao-cta .btn-outline:hover {
  background: rgba(0, 255, 255, 0.08) !important;
  border-color: #00ffff !important;
}

.apresentacao-visual {
  display: flex;
  width: 435px;
  align-items: top;
  padding-top: 0;
  padding-bottom: 0;
  text-align: left;
}

.hero-visual {
  position: relative;
  width: 100%;
}

.hero-visual::before {
  content: "";
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 320px;
  height: 320px;
  background: radial-gradient(
    circle,
    rgba(0, 212, 170, 0.15) 0%,
    transparent 70%
  );
  border-radius: 50%;
  pointer-events: none;
  animation: pulse-glow 4s ease-in-out infinite;
}

@keyframes pulse-glow {
  0%,
  100% {
    opacity: 0.6;
    transform: translate(-50%, -50%) scale(1);
  }
  50% {
    opacity: 1;
    transform: translate(-50%, -50%) scale(1.1);
  }
}

.code-window {
  position: relative;
  background: rgba(12, 12, 22, 0.95);
  border-radius: 20px;
  overflow: hidden;
  border: 1px solid rgba(0, 255, 255, 0.2);
  box-shadow:
    0 25px 60px rgba(0, 0, 0, 0.6),
    0 0 60px rgba(0, 212, 170, 0.1),
    inset 0 1px 0 rgba(255, 255, 255, 0.03);
  backdrop-filter: blur(10px);
  transition:
    transform 0.3s ease,
    box-shadow 0.3s ease;
}

.code-window:hover {
  transform: translateY(-4px);
  box-shadow:
    0 30px 70px rgba(0, 0, 0, 0.65),
    0 0 80px rgba(0, 212, 170, 0.15);
}

.code-header {
  display: flex;
  align-items: center;
  gap: 8px;
  padding: 14px 18px;
  background: rgba(0, 0, 0, 0.3);
  border-bottom: 1px solid rgba(255, 255, 255, 0.06);
}

.code-dot {
  width: 10px;
  height: 10px;
  border-radius: 50%;
  background: #444;
}

.code-dot:nth-child(1) {
  background: #ff5f56;
}
.code-dot:nth-child(2) {
  background: #ffbd2e;
}
.code-dot:nth-child(3) {
  background: #27c93f;
}

.code-title {
  margin-left: 8px;
  font-size: 0.85rem;
  color: #888;
  font-family: monospace;
}

.code-body {
  padding: 1.5rem 1.75rem;
}

.code-body pre {
  margin: 0;
  font-size: 0.95rem;
  line-height: 1.7;
  font-family: "Fira Code", "Consolas", monospace;
  color: #e0e0e0;
}

.code-keyword {
  color: #c678dd;
}
.code-var {
  color: #61afef;
}
.code-prop {
  color: #e06c75;
}
.code-string {
  color: #98c379;
}

.tech-float {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  pointer-events: none;
}

.tech-icon {
  position: absolute !important;
  opacity: 0.35;
  filter: drop-shadow(0px 0px 10px rgb(0, 49, 212));
  transition:
    transform 0.4s ease,
    opacity 0.3s ease;
}

.hero-visual:hover .tech-icon {
  opacity: 0.5;
}

.tech-vue {
  top: -8px;
  right: -15px;
  color: #42b883 !important;
  animation: float 3s ease-in-out infinite;
}
.tech-js {
  bottom: 5px;
  right: -10px;
  color: #f7df1e !important;
  animation: float 3.5s ease-in-out infinite 0.5s;
}
.tech-html {
  bottom: 0;
  left: -20px;
  color: #e34c26 !important;
  animation: float 3.2s ease-in-out infinite 0.3s;
}
.tech-css {
  top: 5px;
  left: -25px;
  color: #264de4 !important;
  animation: float 2.8s ease-in-out infinite 0.7s;
}

@keyframes float {
  0%,
  100% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-8px);
  }
}

@media (max-width: 960px) {
  .apresentacao-visual {
    order: -1;
    padding: 1rem 0 !important;
    justify-content: center;
  }
  .hero-visual {
    max-width: 100%;
    min-width: 0;
  }
}
</style>
