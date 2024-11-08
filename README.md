Projeto de Website para Dra. Patricia Schons
Este é um projeto de website desenvolvido com Vue 3 e Tailwind CSS. O site tem uma estrutura responsiva e moderna com animações, sendo ideal para a apresentação profissional de advogados, escritórios de advocacia, ou outras áreas jurídicas.

Tecnologias Utilizadas
plaintext
Copiar código
- Vue 3: Framework JavaScript progressivo para criar interfaces de usuário.
- Tailwind CSS: Framework CSS para estilização rápida e flexível.
- Lucide Vue: Biblioteca de ícones para Vue.
Estrutura do Projeto
O projeto é composto por uma estrutura Vue 3 Single File Component (SFC) dividida em três seções principais:

plaintext
Copiar código
- Header: Menu de navegação com gradiente de cor.
- Main Content: Inclui seções como "Áreas de Atuação", "Sobre" e "Contato".
- Footer: Contém os direitos autorais e links sociais.
Estrutura do Arquivo
Template
O template define a estrutura HTML da página, dividida em:

plaintext
Copiar código
- Header: Com um menu de navegação responsivo e gradiente de cor.
- Main: Contém as seções de Introdução, Áreas de Atuação, Sobre, e Contato.
- Footer: Inclui direitos autorais e links para redes sociais.
Script
O script usa setup do Vue 3 para definir a lógica:

javascript
Copiar código
- mobileMenuOpen: Define a exibição do menu móvel.
- menuItems: Lista de itens de menu.
- areasAtuacao: Informações sobre as áreas de atuação com ícones e descrições.
- form: Modelo de formulário reativo para a seção de contato.
- handleSubmit: Função que manipula o envio do formulário de contato.
Estilo
Personalizações de estilo são aplicadas usando classes do Tailwind CSS para garantir responsividade e efeitos visuais.

Customização de Configuração
Para mais detalhes de configuração, consulte a Referência de Configuração.
