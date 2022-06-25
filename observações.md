# Disposição do Three.js
É necessário clonar o repositório do GitHub (https://github.com/mrdoob/three.js) e, assim, procurar pelos arquivos **GLTFLoader.js** (three.js-master > examples > jsm > loaders), **thee.js** (thee.js-master > build) e **threemodules.js** (three.js-master > build). Sim, ambos os últimos estão dentro da mesma pasta.

Observação: Baixe o repositório na main/root.

## Live Server
Lembre-se de utilizar a extensão Live Server para visualizar estes arquivos. Basicamente, carregá-los de outra forma pode causar problemas de segurança ("same origin policy").


# Importações e Código | (Issues)
Modifique o final do arquivo GLTFLoader.js (```@import```) na linha ```from```. Tenha certeza que está chamando o diretório que está na sua main/root.
No caso, ```"/.three.modules.js"```. 

**ERROR: Nodejs: Error: ENOENT: no such file or directory**: Node não achou duas pastas inicialmente (SpecularGlosiness e scene.bin). 

Resolução: copiei as pastas da root para dentro do projeto (import three.js) no lugar de deixá-las apenas carregar sozinhas através da importação.

# Câmera
Valores normais da iluminação atmosférica (gradiente light~black at the bottom e intensidade).
```js
var light = new THREE.HemisphereLight(0xffffff, 0x000000, 2)
```

**ERROR**: Inspecionando, descobrimos rapidamente que o navegador não gosta do método ```requestAnimationFrame()```. 

Resolução: forçar o jsdom-global a adicionar o ```requestAnimationFrame()``` como um objeto global. Claro, antes de rodar os testes. 
```js
global.requestAnimationFrame = cb => cb()
```








