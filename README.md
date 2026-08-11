# 3D Monco (beta)

> Modelação & Impressão 3D para crianças do ensino básico e secundário

**3D Monco** é uma ferramenta educativa open-source que permite a crianças dos 6 aos 18 anos criar modelos 3D directamente no browser, exportar para STL e enviar para impressora 3D — tudo sem instalação, sem conta, sem fricção.

🌐 [3d.monco.io](https://3d.monco.io)

---

## O produto

Uma aplicação web single-file (`index.html`) que corre 100% no browser, sem backend, sem dependências de instalação. O aluno abre, desenha e imprime.

### O que é possível fazer

- **Desenhar** formas 2D (rectângulo, círculo, triângulo, estrela, coração, hexágono, seta, trapézio, losango) e forma livre (freehand)
- **Colorir** com a paleta PICO-8 (até 8 cores personalizáveis) — cada cor tem uma espessura de extrusão editável
- **Transformar** formas: mover, escalar, rodar (45° fixo ou livre), deformar, duplicar, apagar
- **Orificios** — modo buraco para criar formas com cavidades
- **Preview 3D** em tempo real com boolean CSG (Clipper.js + Three.js)
- **Exportar STL** com timestamp, pronto para slicer (escala: altura do stage = 200mm)
- **Layers** — painel de camadas com visibilidade e reordenação
- **Conquistas** com confetti e popup central
- **Certificado** exportável como imagem (PNG) com partilha nativa (Web Share API)
- **Guardar/Carregar** composições em JSON
- **Tangram** — puzzle de 7 peças geométricas com botão de gato automático
- **Robot Monco** carregado ao arrancar como logo/mascote

---

## Stack técnica

| Camada | Tecnologia |
|--------|-----------|
| Runtime | Browser nativo (zero backend) |
| 3D engine | Three.js r128 |
| Boolean CSG | Clipper.js 6.4.2 |
| Captura de imagem | html2canvas 1.4.1 |
| UI tokens | Ant Design dark theme (CSS vars) |
| Armazenamento | JSON download/upload (sem cloud) |

**Arquitectura:** ficheiro HTML único (~2700 linhas). Sem build step, sem npm, sem framework.

---

## Como usar

1. Abrir `index.html` num browser moderno (Chrome, Edge, Safari, Firefox)
2. Seleccionar uma forma no painel esquerdo
3. Escolher a cor e espessura de extrusão (duplo clique na cor para editar)
4. Desenhar e transformar no stage
5. Clicar **3D** para preview
6. Clicar **STL** para exportar e enviar para a impressora

---

## Estrutura do ficheiro

```
monco3d_v50_final.html
├── <style>          — CSS completo (Ant Design tokens, layout, componentes)
├── <body>           — HTML (header, lsb, stage, rsb, modais)
└── <script>         — JS inline (~1600 linhas)
    ├── STATE        — variáveis globais (shapes, viewport, ferramentas)
    ├── DRAW         — redraw, shapePath, handles
    ├── EVENTS       — onDown, onMove, onUp, wheel, keyboard
    ├── 3D           — buildMesh3D, clipperToThreeShape, STL export
    ├── ACHIEV.      — conquistas, confetti, certificado
    └── INIT         — loadMonco (robot logo)
```

---

## Roadmap (próximas fases)

### Fase 2 — Professor & Turma
- [ ] Código de turma (acesso por PIN)
- [ ] Dashboard do professor com projetos dos alunos
- [ ] Aprovação para impressão pelo professor
- [ ] Comentários do professor por projeto

### Fase 3 — Certificado & Gamificação
- [ ] Layout do certificado redesenhado
- [ ] Validação/assinatura digital do professor
- [ ] Níveis e badges por tipo de forma usada

### Fase 4 — Cloud & Colaboração
- [ ] Backend: Supabase (piloto) → PocketBase/Hetzner (escala)
- [ ] Projetos guardados na cloud por aluno
- [ ] Galeria de turma

---

## Modelo de negócio

| Segmento | Preço |
|----------|-------|
| Famílias | €59 / ano |
| Turma escolar | €290 / turma / ano |
| Câmara municipal | €5 / aluno (mín. 200) |
| ATL / AEC | €399 / sala / ano |

---

## Autoria

**David Araújo** — CEO, Monco.io  
Portugal · [monco.io](https://monco.io)

Apoiar o projecto: [☕ Ko-fi](https://ko-fi.com/monco)

---

## Licença

MIT — livre para usar, modificar e distribuir com atribuição.

```
Copyright (c) 2025 David Araújo / Monco.io
```
