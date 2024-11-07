<template>
  <!-- Container principal com altura mínima e fundo claro -->
  <div class="min-h-screen bg-gray-100">
    <!-- Cabeçalho com gradiente e sombra -->
    <header class="bg-gradient-to-r from-purple-600 to-indigo-600 text-white shadow-lg">
      <!-- Navegação dentro do cabeçalho -->
      <nav class="container mx-auto px-6 py-3">
        <div class="flex justify-between items-center">
          <!-- Título do cabeçalho -->
          <div class="text-2xl font-bold">Dra. Patricia Schons</div>
          <!-- Links do menu para desktop -->
          <div class="hidden md:flex space-x-4">
            <a v-for="item in menuItems" :key="item.id" :href="item.href" class="hover:text-purple-200 transition duration-300">
              {{ item.name }}
            </a>
          </div>
          <!-- Botão de menu para dispositivos móveis -->
          <button @click="toggleMobileMenu" class="md:hidden">
            <Menu v-if="!mobileMenuOpen" class="h-6 w-6" />
            <X v-else class="h-6 w-6" />
          </button>
        </div>
      </nav>
      <!-- Menu móvel com animação de transição -->
      <transition name="slide-fade">
        <div v-if="mobileMenuOpen" class="md:hidden">
          <a v-for="item in menuItems" :key="item.id" :href="item.href" class="block py-2 px-4 text-sm hover:bg-purple-700">
            {{ item.name }}
          </a>
        </div>
      </transition>
    </header>
    <!-- Conteúdo principal -->
    <main>
      <!-- Seção de introdução com gradiente, título e CTA -->
      <section class="bg-gradient-to-r from-purple-600 to-indigo-600 text-white py-20">
        <div class="container mx-auto px-6">
          <div class="flex flex-col md:flex-row items-center">
            <!-- Texto principal e botão de contato -->
            <div class="md:w-1/2 mb-8 md:mb-0 text-center md:text-left">
              <h1 class="text-4xl md:text-6xl font-bold mb-4">Justiça com Excelência</h1>
              <p class="text-xl mb-8">Defendendo seus direitos com projetos e expertise.</p>
              <a href="#contato" class="bg-white text-purple-600 py-3 px-6 rounded-full font-bold hover:bg-purple-100 transition duration-300"> Entre em Contato </a>
            </div>
            <!-- Imagem de perfil com sombra e efeito de redimensionamento responsivo -->
            <div class="md:w-1/2 flex justify-center">
              <img alt="Perfil" src="../assets/pati.png?height=400&width=400" class="rounded-full shadow-2xl transform hover:scale-105 transition duration-500">
            </div>
          </div>
        </div>
      </section>
      <!-- Seção de áreas de atuação -->
      <section id="areas" class="py-20">
        <div class="container mx-auto px-6">
          <h2 class="text-3xl font-bold text-center mb-12">Áreas de Atuação</h2>
          <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
            <div v-for="area in areasAtuacao" :key="area.id" class="bg-white rounded-lg shadow-md p-6 hover:shadow-xl transition duration-300">
              <component :is="area.icon" class="h-12 w-12 text-purple-600 mb-4" />
              <h3 class="text-xl font-semibold mb-2">{{ area.name }}</h3>
              <p class="text-gray-600">{{ area.description }}</p>
            </div>
          </div>
        </div>
      </section>
      <!-- Seção sobre a Dra. Patricia com layout e imagem -->
      <section id="sobre" class="bg-gray-100 py-20">
        <div class="container mx-auto px-6">
          <div class="flex flex-col md:flex-row items-center">
            <!-- Imagem de perfil com centralização e efeito de sombra -->
            <div class="md:w-1/2 mb-8 md:mb-0 flex justify-center">
              <img alt="Perfil" src="../assets/pati.png?height=400&width=400" class="rounded-full shadow-2xl transform hover:scale-105 transition duration-500">
            </div>
            <!-- Texto sobre a Dra. Patricia e links sociais -->
            <div class="md:w-1/2 md:pl-12 text-center md:text-left">
              <h2 class="text-3xl font-bold mb-6">Sobre Dra. Patricia Schons</h2>
              <p class="text-gray-700 mb-4">Com mais de 15 anos de experiência, Dra. Patricia Schons se destaca em casos complexos e de alta relevância.</p>
              <p class="text-gray-700 mb-6">Seu compromisso com a justiça e atenção aos detalhes fazem dela uma profissional respeitosa e confiável.</p>
              <div class="flex justify-center md:justify-start space-x-4">
                <a href="#" class="text-purple-600 hover:text-purple-800">
                  <Linkedin class="h-6 w-6" />
                </a>
                <a href="#" class="text-purple-600 hover:text-purple-800">
                  <Twitter class="h-6 w-6" />
                </a>
              </div>
            </div>
          </div>
        </div>
      </section>
      <!-- Seção de contato com formulário -->
      <section id="contato" class="py-20">
        <div class="container mx-auto px-6">
          <h2 class="text-3xl font-bold text-center mb-12">Entre em Contato</h2>
          <form @submit.prevent="handleSubmit" class="max-w-lg mx-auto">
            <div class="mb-6">
              <label for="name" class="block text-gray-700 font-bold mb-2">Nome</label>
              <input type="text" id="name" v-model="form.name" required class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-purple-600" />
            </div>
            <div class="mb-6">
              <label for="email" class="block text-gray-700 font-bold mb-2">E-mail</label>
              <input type="email" id="email" v-model="form.email" required class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-purple-600" />
            </div>
            <div class="mb-6">
              <label for="message" class="block text-gray-700 font-bold mb-2">Mensagem</label>
              <textarea id="message" v-model="form.message" required rows="4" class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-purple-600"></textarea>
            </div>
            <button type="submit" class="w-full bg-purple-600 text-white py-3 px-6 rounded-md font-bold hover:bg-purple-700 transition duration-300"> Enviar Mensagem </button>
          </form>
        </div>
      </section>
    </main>
    <!-- Rodapé com direitos autorais e links sociais -->
    <footer class="bg-gray-800 text-white py-8">
      <div class="container mx-auto px-6">
        <div class="flex flex-col md:flex-row justify-between items-center">
          <div class="mb-4 md:mb-0 text-center md:text-left">
            <p>© 2024 Dra. Patricia Schons. Todos os direitos reservados.</p>
            <a href="https://www.cleberdelgado.com.br" class="hover:text-purple-400">Desenvolvido por Cleber Delgado</a>
          </div>
          <div class="flex space-x-4">
            <a href="#" class="hover:text-purple-400 transition duration-300">
              <Facebook class="h-6 w-6" />
            </a>
            <a href="#" class="hover:text-purple-400 transition duration-300">
              <Instagram class="h-6 w-6" />
            </a>
            <a href="#" class="hover:text-purple-400 transition duration-300">
              <Linkedin class="h-6 w-6" />
            </a>
          </div>
        </div>
      </div>
    </footer>
  </div>
</template>

<script setup>
import { ref, reactive } from 'vue';
import { Menu, X, Linkedin, Twitter, Facebook, Instagram, Scale, Home, Briefcase } from 'lucide-vue-next';

const mobileMenuOpen = ref(false);
const toggleMobileMenu = () => {
  mobileMenuOpen.value = !mobileMenuOpen.value;
};

const menuItems = [
  { id: 1, name: 'Início', href: '#' },
  { id: 2, name: 'Áreas de Atuação', href: '#areas' },
  { id: 3, name: 'Sobre', href: '#sobre' },
  { id: 4, name: 'Contato', href: '#contato' },
];

const areasAtuacao = [
  { id: 1, name: 'Direito Previdenciario', icon: Scale, description: 'Aposentadorias e benefícios sociais.' },
  { id: 2, name: 'Direito de Família', icon: Home, description: 'Assessoria em subsídios, guarda de filhos e partilha de bens.' },
  { id: 3, name: 'Direito Trabalhista', icon: Briefcase, description: 'Defesa dos direitos dos trabalhadores e empregadores.' },
];

const form = reactive({
  name: '',
  email: '',
  message: '',
});

const handleSubmit = () => {
  console.log(form);
};
</script>

<style scoped>
/* Centralize imagens de perfil e ajuste efeitos */
.img-container {
  display: flex;
  justify-content: center;
  transition: transform 0.3s ease-in-out;
}

.img-container:hover {
  transform: scale(1.05);
}
</style>
