# mypolyserve

    cd ~/bin
    git clone https://github.com/joao-parana/mypolyserve.git


Ou, se não desejar clonar o repositório:

    cd ~/bin
    curl -o xx.zip https://codeload.github.com/joao-parana/mypolyserve/zip/v1.0 \
         && unzip xx.zip \
         && rm xx.zip \
         && mv mypolyserve-1.0/* . \
         && mv mypolyserve-1.0/.gitignore . \
         && rmdir mypolyserve-1.0


É necessário executar os comandos abaixo para instalar as dependências: 

    cd ~/bin 
    pwd # para verificar !
    npm install resolve minimist polyserve 

Depois é só se posicionar no diretório do seu componente e executar:

    mypolyserve

O fonte `mypolyserve` pode ser ajustado para fazer pós processamento 
pois o polyserve à partir da versão 0.5 retorna um objeto Promise. 
Observe que estou executando um comando `console.log()` no primeiro passo 
`then`. Isso pode ser substituido por algo mais útil, tal como executar 
um WebSocketServer para testar o componente, caso ele necessite. 
Neste caso `sampledata`  pode ser passado para o mypolyserve melhorando 
a inversão de controle

Exemplo de pós-processamento :

    // Here I use the server created by polyserve, and attatch the
    // websocket server to it

    var socketServer = new WebSocketServer({server: server});
    socketServer.on("connection", function(){
        // Generating sampledata
       socketServer.send(sampledata, function(){});
    });

