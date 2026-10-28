# Dra. Maria Marta Andrade — Landing page

React + TypeScript + Vite + Tailwind CSS + Lucide. Aplicação estática, sem backend, serviços pagos, formulário, analytics, cookies de rastreamento ou mapa incorporado. Links externos só são acionados pelo visitante.

## Executar

Requer Node.js 20.19+ ou 22.12+.

```sh
npm install
npm run dev
```

Abra o endereço exibido pelo Vite (normalmente http://localhost:5173).

```sh
npm run build
npm run preview
```

Saída estática: `dist/`. Não abra o HTML por `file://`: use o servidor de preview.

## Configuração central

Edite `src/clinic.ts`. Os tratamentos também estão centralizados nesse arquivo.

- `cro`: vazio por padrão. Inserir o registro completo e UF após confirmação. O campo será apresentado na seção Sobre e no rodapé; vazio, nenhum rótulo ou dado fictício aparece.
- `phone`, `phoneDisplay`, `phoneConfirmed`: telefone de referência informado no briefing, ainda provisório. O site informa essa condição antes da ligação. Só marque confirmado após validação.
- `whatsapp`, `whatsappConfirmed`: número internacional, com DDI e DDD; ambos devem estar preenchidos/confirmados para abrir WhatsApp e exibir o botão flutuante. Nunca presumir que o telefone de referência é WhatsApp.
- `address`, `city`, `mapsAddress`, `days`: endereço, Google Maps e dias. Não foram criados horários específicos.
- `logo`: copie a logomarca original para `public/assets/logo.webp` e defina `/assets/logo.webp`. A imagem anexada no chat não estava montada como arquivo no workspace. Até sua inserção, aparece apenas a identificação textual da profissional, sem logotipo genérico ou redesenho. A mesma imagem será usada como favicon e imagem OG. Para melhor qualidade, pode-se substituir o favicon por exportação reduzida autorizada da marca.
- `canonical`: URL HTTPS definitiva. Ativa canonical e Schema.org Dentist com endereço confirmado; telefone só entra no schema quando confirmado. Logo ativa imagem OG. Sitemap não foi gerado porque a URL final ainda não existe. Após definição, pode criar `public/robots.txt` e `public/sitemap.xml` com a URL canônica e refazer o build. Não publicar sitemap com endereço fictício.
- `developerCredit`: crédito discreto, removível definindo string vazia.

Reexecute o build após qualquer alteração. Conteúdo de contato, CRO e endereço não precisa ser alterado em componentes.

## Pendências antes da publicação definitiva

1. Verificar e inserir o CRO profissional correto, incluindo UF, e revisar os elementos obrigatórios conforme as exigências aplicáveis à publicidade odontológica (CFO/CRO). O projeto não certifica conformidade jurídica.
2. Confirmar o telefone provisório +55 88 8229-2109 e, separadamente, se existe WhatsApp autorizado.
3. Inserir o arquivo original da logo e conferir seu uso em desktop, celular, favicon e compartilhamento.
4. Configurar domínio/canonical, gerar sitemap e revisar os dados com a responsável.

Não foram inventados registros, especializações, avaliações, depoimentos, preços, equipamentos, experiência, fotos ou resultados. A demo antiga Aura foi preservada. Esta versão não foi publicada como site definitivo.

## Cloudflare Pages

### Upload direto, sem GitHub

Execute `npm run build`. No Cloudflare, abra Workers & Pages → Create application → Pages → Upload assets. Envie o conteúdo de `dist/` (ou o ZIP estático fornecido), não o projeto-fonte nem `node_modules`. Escolha o domínio após a revisão das pendências acima. A plataforma não precisa executar Node em produção.

### Integração com Git (opcional)

Selecione o repositório e use framework Vite, comando `npm run build`, diretório de saída `dist`, raiz do projeto atual. Nenhuma integração com GitHub foi criada nesta entrega.

## Verificação

Build TypeScript + Vite aprovado. Servidor de desenvolvimento respondeu HTTP 200. Chromium automatizado: larguras 320, 390, 768 e 1440 px sem overflow horizontal; seis tratamentos; menu mobile abre, navega e fecha; modal de contato e fechamento por Escape; FAQ; âncoras; CRO e WhatsApp ocultos enquanto vazios; prefers-reduced-motion; nenhum erro JS observado. Revisão visual de capturas desktop e mobile. Ligações e destino externo do Maps não foram efetivamente acionados; confirme a titularidade do número. Não houve auditoria formal de acessibilidade nem medição real de Core Web Vitals.
