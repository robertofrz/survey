# Guia de Respostas - Entrevista React Junior Octaprice

## Apresentação Pessoal e Conexão com a Empresa

### Como você conheceu a empresa
"Conheci a Octaprice através do Reddit, onde postei sobre meus desafios como desenvolvedor júnior e minha paixão por front-end. O que mais me chamou atenção na empresa foi o foco em inteligência de precificação e soluções baseadas em IA - é exatamente o tipo de tecnologia inovadora que me motiva a trabalhar na área."

### Sobre sua experiência anterior
"Trabalhei mais de 10 anos no atendimento ao público no Brasil, Irlanda e Portugal, em varejo e cafeteria. Isso me ensinou a lidar com pessoas diferentes, a trabalhar sob pressão e em equipe, sempre com foco em resultados. Essa experiência me deu uma base sólida para entender as necessidades do usuário final, o que considero essencial no desenvolvimento front-end."

### Por que escolheu desenvolvimento web
"Escolhi essa área porque tem muito futuro, mesmo achando difícil no começo. Depois de quase um ano estudando, estou orgulhoso do que aprendi e gosto muito do que faço. Agora só preciso de uma chance para mostrar meu potencial e crescer na carreira."

## Questões Técnicas React

### 1. O que é o React e como você o descreveria?
"O React é uma biblioteca JavaScript criada pelo Facebook para construir interfaces de usuário, especialmente para aplicações web. Eu o descreveria como uma ferramenta que permite criar componentes reutilizáveis e gerenciar o estado da aplicação de forma eficiente. O que mais gosto no React é sua abordagem declarativa - você descreve como a interface deve parecer em diferentes estados, e o React cuida de atualizar o DOM de forma otimizada."

### 2. Principais funcionalidades do React
"As principais funcionalidades são: componentes reutilizáveis, Virtual DOM para performance, JSX para escrever HTML no JavaScript, sistema de props e state para gerenciar dados, hooks para lógica de estado em componentes funcionais, e um ecossistema rico de bibliotecas. Nos meus projetos, uso muito essas funcionalidades - por exemplo, no SkyWatch criei componentes reutilizáveis para diferentes tipos de cards de clima."

### 3. O que é JSX e por que é utilizado?
"JSX é uma extensão de sintaxe do JavaScript que permite escrever elementos HTML diretamente no código JS. É utilizado porque torna o código mais legível e intuitivo - em vez de usar createElement, podemos escrever tags HTML normalmente. Por exemplo, `<div>Hello World</div>` é muito mais claro que `React.createElement('div', null, 'Hello World')`."

### 4. Os navegadores conseguem interpretar JSX diretamente?
"Não, os navegadores não interpretam JSX nativamente. O JSX precisa ser transpilado para JavaScript puro usando ferramentas como Babel. Nos meus projetos, uso Vite que já vem com essa configuração, então o JSX é automaticamente convertido para chamadas React.createElement durante o build."

### 5. O que é o Virtual DOM? Vantagens e desvantagens
"O Virtual DOM é uma representação em memória do DOM real. Quando o state muda, o React cria um novo Virtual DOM, compara com o anterior, e atualiza apenas as partes que mudaram no DOM real. 

Vantagens: performance melhor em aplicações complexas, abstração que facilita o desenvolvimento, permite otimizações automáticas.

Desvantagens: overhead de memória, pode ser desnecessário para aplicações muito simples, curva de aprendizado inicial."

### 6. Diferença entre componentes funcionais e de classe
"Componentes de classe eram a forma tradicional, usando `class extends React.Component` e métodos como `render()`. Componentes funcionais são funções que retornam JSX. Com a introdução dos hooks, componentes funcionais se tornaram mais poderosos e são agora a abordagem recomendada. Eu uso exclusivamente componentes funcionais nos meus projetos porque são mais simples, têm menos boilerplate e são mais fáceis de testar."

### 7. Props e State - Diferenças
"Props são dados passados de um componente pai para filho - são imutáveis no componente que as recebe. State é o estado interno do componente, que pode ser modificado e causa re-renderização quando muda. No meu projeto codeHire, uso props para passar dados do currículo entre componentes e state para gerenciar o que está sendo editado no momento."

### 8. Ciclo de vida com hooks
"Em componentes funcionais, usamos hooks para gerenciar o ciclo de vida:
- `useEffect` sem dependências = componentDidMount
- `useEffect` com dependências = componentDidUpdate
- `useEffect` com cleanup = componentWillUnmount
- `useState` para gerenciar estado local

Por exemplo, no SkyWatch uso `useEffect` para buscar dados do clima quando o componente monta."

### 9. React Portals
"React Portals permitem renderizar componentes fora da hierarquia normal do DOM, em qualquer nó DOM. São úteis para modais, tooltips, ou dropdowns que precisam escapar do overflow do container pai. Uso quando preciso garantir que um modal apareça acima de todos os outros elementos, independente da estrutura CSS."

### 10. React Fiber
"React Fiber é a reimplementação do algoritmo de reconciliação do React, introduzido na versão 16. Permite interrupção e priorização de atualizações, melhorando a responsividade da interface. Embora trabalhe por baixo dos panos, nos beneficia com melhor performance em aplicações complexas."

## Hooks

### 15. React Hooks e por que foram introduzidos
"Hooks foram introduzidos para permitir usar state e outras funcionalidades do React em componentes funcionais, eliminando a necessidade de classes. Resolvem problemas como reutilização de lógica stateful, componentes complexos difíceis de entender, e confusão com `this` em classes."

### 16. Hooks mais utilizados
"Os mais comuns são:
- `useState` para estado local
- `useEffect` para efeitos colaterais
- `useContext` para consumir context
- `useMemo` e `useCallback` para otimização
- `useRef` para referencias DOM
- `useReducer` para estados complexos"

### 17. Como funciona o useState
"useState retorna um array com o valor atual e uma função para atualizá-lo. Exemplo:
```javascript
const [count, setCount] = useState(0);
```
A função setter pode receber um valor direto ou uma função que recebe o valor anterior."

### 18. useEffect e métodos de ciclo de vida
"useEffect combina componentDidMount, componentDidUpdate e componentWillUnmount:
```javascript
useEffect(() => {
  // efeito
  return () => {
    // cleanup
  };
}, [dependencies]);
```
As dependências controlam quando o efeito executa. Array vazio = só no mount, sem array = toda renderização."

### 19. useRef vs useState
"useRef cria uma referência mutável que persiste entre renderizações, mas mudanças nela não causam re-render. useState causa re-renderização quando muda. useRef é útil para acessar elementos DOM ou armazenar valores que não afetam a UI."

### 20. useMemo
"useMemo memoriza o resultado de um cálculo caro, recalculando apenas quando as dependências mudam. Uso quando tenho operações custosas que não precisam ser executadas a cada render:
```javascript
const expensiveValue = useMemo(() => heavyCalculation(data), [data]);
```

### 21. useCallback
"useCallback memoriza uma função, criando uma nova apenas quando as dependências mudam. Útil para evitar re-renders desnecessários quando passamos funções como props:
```javascript
const memoizedCallback = useCallback(() => {
  doSomething(a, b);
}, [a, b]);
```

### 22. useContext
"useContext permite consumir valores de um Context sem precisar do Consumer. Simplifica o acesso a dados globais:
```javascript
const theme = useContext(ThemeContext);
```
Uso bastante nos meus projetos para temas e autenticação."

### 23. Custom Hooks
"Custom hooks são funções que encapsulam lógica stateful reutilizável. Começam com 'use' e podem usar outros hooks. Criei um custom hook no SkyWatch para gerenciar geolocalização:
```javascript
function useGeolocation() {
  const [location, setLocation] = useState(null);
  const [error, setError] = useState(null);
  // lógica de geolocalização
  return { location, error };
}
```

### 24. Regras dos Hooks
"As regras são:
1. Só chame hooks no nível superior - nunca dentro de loops, condições ou funções aninhadas
2. Só chame hooks em componentes React ou custom hooks
Essas regras garantem que os hooks sejam chamados na mesma ordem a cada renderização."

## Gerenciamento de Estado

### 27. State Management
"Gerenciamento de estado é como organizamos e controlamos os dados da aplicação. Pode ser local (useState), global (Context API, Redux), ou bibliotecas especializadas. A escolha depende da complexidade e escopo dos dados."

### 28. Bibliotecas de gerenciamento de estado
"As principais são:
- Redux/Redux Toolkit para aplicações complexas
- Zustand para simplicidade e performance
- Jotai para estado atômico
- Context API nativa do React
- React Query para estado de servidor
Já usei Zustand e Context API nos meus projetos."

### 29. Quando usar Context API vs bibliotecas externas
"Context API é ótima para:
- Dados que mudam pouco (tema, auth)
- Aplicações pequenas/médias
- Quando queremos evitar dependências externas

Bibliotecas como Redux/Zustand para:
- Estados complexos com muitas interações
- Aplicações grandes
- Quando precisamos de DevTools avançadas
- Time travel debugging"

### 30. Prop Drilling
"Prop drilling é passar props através de vários níveis de componentes só para chegar ao componente que realmente precisa. Evito usando Context API, custom hooks, ou bibliotecas de estado global. No codeHire, uso Context para dados do currículo que vários componentes precisam acessar."

## Performance e Otimização

### 39. Principais preocupações de performance
"As principais são:
- Re-renders desnecessários
- Bundlers grandes
- Carregamento inicial lento
- Memory leaks
- Operações custosas sem memorização
- Listas grandes sem virtualização"

### 40. Técnicas de otimização
"Uso várias técnicas:
- React.memo para componentes
- useMemo/useCallback para cálculos e funções
- Lazy loading com React.lazy
- Code splitting
- Otimização de imagens
- Bundle analysis
No SoloDev implementei cache no servidor e lazy loading para melhorar performance."

### 41. Memoização
"Memoização é armazenar resultados de operações caras para evitar recálculos. No React, usamos useMemo para valores e useCallback para funções. Ajuda evitando trabalho desnecessário quando as dependências não mudaram."

## Roteamento

### 42. React Router
"React Router permite navegação SPA. Defino rotas com Route components, uso BrowserRouter como wrapper, e navego programaticamente com useNavigate. Implementei no SoloDev para diferentes seções da plataforma."

### 43. BrowserRouter
"BrowserRouter usa HTML5 History API para roteamento, criando URLs limpos sem hash. É o wrapper principal que habilita roteamento na aplicação."

### 44. useNavigate e useParams
"useNavigate permite navegação programática: `navigate('/path')`. useParams extrai parâmetros da URL: se a rota é `/user/:id`, useParams retorna `{id: 'valor'}`."

## Tratamento de Erros

### 45-46. Error Boundaries
"Error Boundaries são componentes que capturam erros JavaScript em qualquer lugar da árvore de componentes. Implemento para evitar que a aplicação toda quebre por um erro localizado. Mostro uma UI de fallback amigável ao usuário."

### 47. Strict Mode
"Strict Mode ajuda identificar problemas potenciais executando alguns códigos duas vezes em desenvolvimento. Detecta side effects inseguros, warns sobre APIs depreciadas, e ajuda com boas práticas."

## Frontend Fundamentals

### 56-66. HTML/CSS
"Estruturo páginas com HTML semântico (header, nav, main, article, section). Uso CSS Grid para layouts bidimensionais e Flexbox para alinhamento unidimensional. Entendo especificidade CSS e uso pseudoclasses. No React, prefiro CSS Modules ou Tailwind - que uso bastante nos meus projetos pela produtividade e consistência."

### 65-66. Responsividade
"Responsividade é fazer layouts que funcionem bem em qualquer tamanho de tela. Uso mobile-first approach, media queries, unidades relativas (rem, %, vw/vh), e testo em diferentes dispositivos. No SkyWatch, criei uma interface que funciona perfeitamente tanto no desktop quanto mobile."

## JavaScript Fundamentals

### 67. var, let, const
"var tem function scope e hoisting; let tem block scope; const é imutável após declaração. Uso const por padrão, let quando preciso reatribuir, e evito var por ser fonte de bugs."

### 68. Arrow Functions
"Arrow functions são mais concisas e não têm seu próprio `this`. Úteis para callbacks e quando queremos manter o contexto do `this` do escopo pai."

### 69. Destructuring
"Destructuring extrai valores de arrays/objetos:
```javascript
const {name, age} = user;
const [first, second] = array;
```
Uso muito com props e state no React."

### 70. Spread/Rest Operator
"Spread (...) expande arrays/objetos. Rest agrupa argumentos em array. Uso para copiar estados imutavelmente no React:
```javascript
setState({...state, newProp: value});
```

### 72. Callbacks, Promises, async/await
"Callbacks são funções passadas como argumentos. Promises representam operações assíncronas. Async/await é sintaxe mais limpa para Promises. Nos meus projetos uso async/await para APIs:
```javascript
const fetchWeather = async (city) => {
  try {
    const response = await fetch(`/api/weather/${city}`);
    return await response.json();
  } catch (error) {
    console.error(error);
  }
};
```

## Ferramentas e Workflow

### 78. Git
"Sim, uso Git diariamente. Sei clonar repositórios, fazer commits com mensagens descritivas, criar branches para features, fazer merge/rebase, e resolver conflitos. Todos meus projetos estão no GitHub."

### 79. npm start
"Sim, uso npm start para rodar projetos localmente. Também uso npm install para dependências, npm build para produção, e entendo scripts customizados no package.json."

### 80. Gerenciadores de pacotes
"Uso principalmente npm, mas também tenho experiência com yarn. Entendo a diferença entre dependencies e devDependencies, uso package-lock.json para versionamento consistente."

### 81. ESLint e Prettier
"ESLint analisa código para encontrar problemas e enforce padrões. Prettier formata código automaticamente. Uso ambos nos projetos para manter consistência e qualidade. Configuro no VSCode para formatar ao salvar."

### 82. Bundling
"Uso principalmente Vite nos projetos React pela velocidade e configuração simples. Já trabalhei com Webpack também. Entendo code splitting, lazy loading, e otimização de bundle size."

## Experiência Prática

### 83. Projetos com React
"Tenho alguns projetos pessoais que me ajudaram bastante a consolidar meus conhecimentos em React e a explorar ferramentas modernas do ecossistema. O primeiro é o SoloDev, que foi também meu primeiro projeto usando Next.js. Eu escolhi o Next porque queria trabalhar com server-side rendering e melhorar a performance e o SEO da aplicação. A ideia da plataforma é ajudar devs a aprenderem de forma mais prática, integrando tutoriais do YouTube, resultados de busca, resumos gerados por IA e perguntas de prática. Também implementei autenticação com Clerk e cache no servidor pra garantir uma experiência fluida. 

O segundo projeto é o SkyWatch, um app de previsão do tempo rápido e responsivo, que usa a geolocalização do usuário, permite buscar cidades, alternar entre Celsius e Fahrenheit e salvar favoritas — tudo com uma pegada mobile-first. 

E por último, o codeHire, que é um construtor de currículos focado em profissionais de tecnologia. Ele tem edição em tempo real, exportação para PDF, dicas sobre como otimizar o currículo para sistemas de rastreamento (ATS) e uma estrutura pensada tanto para quem está buscando vaga quanto para times de RH. 

Em todos esses projetos, trabalhei com React (usando Vite ou Next), além de ferramentas como Zustand, React Query, Context API e boas práticas de design responsivo."

## Questões Comportamentais

### 84. Prazos apertados
"Minha experiência no atendimento me ensinou a trabalhar sob pressão. Priorizo as funcionalidades mais importantes, comunico proativamente sobre o status, e se necessário, proponho MVPs que entregam valor rapidamente. Prefiro entregar algo funcional do que algo incompleto."

### 85. Trabalho em equipe vs sozinho
"Gosto de ambos. Trabalhando sozinho consigo focar e ser produtivo, mas em equipe aprendo muito com os outros e conseguimos resolver problemas mais complexos. Minha experiência no atendimento me deu habilidades de comunicação que ajudam no trabalho colaborativo."

### 86. Como aprende coisas novas
"Combino documentação oficial, tutoriais práticos, projetos pessoais e comunidades como Reddit e Discord. Quando tenho dúvidas, procuro na documentação primeiro, depois Stack Overflow, e se ainda assim não resolver, pergunto em comunidades. Sempre procuro entender o 'porquê' além do 'como'."

### 87. Pedir ajuda e code review
"Sim, acredito que pedir ajuda é fundamental para crescer. No início era mais difícil, mas aprendi que todos passam por isso. Code review é essencial - mesmo nos projetos pessoais, procuro feedback em comunidades. Estou sempre aberto a sugestões e críticas construtivas."

## Fechamento da Entrevista

### Mensagem sobre o TCC encontrado
"Aliás, pesquisando sobre a empresa, encontrei seu trabalho de conclusão sobre microsserviços na USP. Eu achei muito legal como você escolheu um tema super atual e importante, que é microsserviços, e conseguiu explicar de um jeito bem prático e didático. Eu ainda estou começando na área, então não conhecia tão bem termos como aplicação monolítica ou microsserviços, mas ao ler seu projeto e pesquisar um pouco, entendi como essa abordagem é fundamental para construir sistemas grandes hoje em dia. Gostei demais da ideia de transformar isso em um ambiente de aprendizado, e me sinto motivado a aprender com alguém que tem essa visão."

### Por que quer trabalhar na Octaprice
"O que mais me atrai na Octaprice é a oportunidade de trabalhar com tecnologias modernas em um produto que realmente impacta o mercado. A inteligência de precificação é um desafio técnico fascinante, e poder contribuir para uma solução que ajuda empresas a tomar decisões melhores seria muito gratificante. Além disso, trabalhar diretamente com o fundador seria uma oportunidade única de aprendizado e crescimento."

### Expectativas
"Espero contribuir com meu conhecimento em React e front-end, aprender sobre o negócio de inteligência de preços, e crescer como desenvolvedor. Estou animado para enfrentar desafios reais e fazer parte de uma equipe que está construindo algo inovador no mercado brasileiro."
