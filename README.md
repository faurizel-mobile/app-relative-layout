# App Relative Layout

Aplicativo Android desenvolvido em Kotlin para demonstrar o uso de `RelativeLayout` e o ajuste de `WindowInsets` para compatibilidade com a área segura do sistema (status bar, navigation bar e edge-to-edge).

## Objetivo

Este projeto foi criado como exemplo didático para aulas de desenvolvimento Android, abordando:

- criação de interfaces com `RelativeLayout`;
- uso de `MainActivity` para carregar o layout;
- ajuste de padding com `WindowInsetsCompat`;
- conceito de `edge-to-edge` em apps modernos;
- organização básica de um projeto Android em Kotlin.

## Tecnologias

- Kotlin
- Android SDK
- AndroidX
- AppCompat
- Material Components
- ViewCompat / WindowInsetsCompat

## Estrutura do projeto

```text
app-relative-layout/
├── .gitignore
├── build.gradle.kts
├── proguard-rules.pro
├── src/
│   ├── androidTest/
│   ├── main/
│   │   ├── AndroidManifest.xml
│   │   ├── java/
│   │   │   └── br/gov/sp/relativelayout/
│   │   │       └── MainActivity.kt
│   │   └── res/
│   │       ├── drawable/
│   │       ├── layout/
│   │       ├── mipmap*/
│   │       ├── values/
│   │       └── xml/
│   └── test/
└── gradle.properties
```

## Como executar

### Pré-requisitos

- Android Studio
- JDK 11
- Android SDK configurado
- Emulador Android ou dispositivo físico

### Passo a passo

1. Clone o repositório:

```bash
git clone https://github.com/faurizel-mobile/app-relative-layout.git
cd app-relative-layout
```

2. Abra o projeto no Android Studio:

- File → Open
- Selecione a pasta do projeto
- Aguarde o Gradle sincronizar

3. Configure o SDK:

- Verifique se o Android Studio detectou o SDK corretamente
- Garanta que a linguagem do projeto está configurada para Kotlin

4. Execute o app:

- Selecione um emulador ou um dispositivo conectado
- Clique em Run → app

5. Para compilar pela linha de comando:

```bash
./gradlew assembleDebug
```

6. Para instalar no dispositivo conectado:

```bash
./gradlew installDebug
```

## Arquivos principais

### `MainActivity.kt`

O arquivo principal da atividade que inicializa a interface:

```kotlin
class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        enableEdgeToEdge()
        setContentView(R.layout.activity_main)
        ViewCompat.setOnApplyWindowInsetsListener(findViewById(R.id.main)) { v, insets ->
            val systemBars = insets.getInsets(WindowInsetsCompat.Type.systemBars())
            v.setPadding(systemBars.left, systemBars.top, systemBars.right, systemBars.bottom)
            insets
        }
    }
}
```

Esse trecho faz o seguinte:

- `enableEdgeToEdge()`: permite que a interface use a tela inteira;
- `setContentView(...)`: carrega o layout XML;
- `ViewCompat.setOnApplyWindowInsetsListener(...)`: ajusta o padding para não sobrepor a região das barras do sistema.

### `activity_main.xml`

Layout principal do app, com a estrutura visual da tela. Em um projeto Android, este arquivo fica em:

```text
src/main/res/layout/activity_main.xml
```

Ele é usado pela atividade principal e pode ser alterado para incluir textos, botões, imagens e outros componentes visuais.

## Como funciona o app

A aplicação abre uma tela inicial com um layout carregado pela activity. Quando a tela é exibida, o código aplica um ajuste de padding para respeitar as barras do sistema. Esse comportamento é importante em dispositivos modernos, pois evita que elementos do layout fiquem cobertos pela status bar, navigation bar ou notch.

## Passo a passo para usar em aula

### Aula 1 - Introdução ao Android e layouts

1. Explique o que é um projeto Android em Kotlin.
2. Mostre a estrutura da pasta `src/main`.
3. Abra `build.gradle.kts` e explique os módulos e dependências.
4. Mostre a relação entre `MainActivity.kt` e `activity_main.xml`.

### Aula 2 - RelativeLayout e edge-to-edge

1. Abra o layout XML e identifique os elementos visuais.
2. Explique a função do `RelativeLayout`.
3. Mostre como `MainActivity` aplica `WindowInsets` para ajustar a UI.
4. Execute o app no emulador e observe o comportamento visual.

### Aula 3 - Prática guiada

Proponha aos alunos pequenas alterações, como:

- adicionar um `TextView` com título;
- adicionar um botão abaixo do texto;
- mudar a cor de fundo da tela;
- alterar o padding e observar o resultado.

## Exercícios sugeridos

- Criar uma tela com três elementos alinhados usando `RelativeLayout`.
- Ajustar a margem de um bloco para ficar sempre visível acima da barra de navegação.
- Criar uma segunda tela e navegar entre elas.
- Aplicar um tema personalizado com cores da instituição ou do projeto.

## Observações

Este repositório é um exemplo simples e didático. Ele foi pensado para facilitar o entendimento de:

- organização básica de um app Android;
- uso de layouts em Kotlin;
- compatibilidade com barras do sistema;
- introdução ao desenvolvimento mobile com Android.

## Licença

Este projeto não possui uma licença específica definida no repositório. Verifique a política do repositório antes de reutilizar o código em produção.

## Autor

Projeto disponível em:

https://github.com/faurizel-mobile/app-relative-layout

---

Se quiser, posso também gerar uma versão em formato de slide para aula, uma versão mais curta para apresentação em GitHub ou um README com foco em `RelativeLayout` para uso em sala de aula.
