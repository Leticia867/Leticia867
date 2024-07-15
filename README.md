função  assíncrona enviarScript ( scriptText )  {
    const  linhas  =  scriptText . split ( '\n' ) . map ( linha  =>  linha . trim ( ) ) . filter ( linha  =>  linha ) ;

    const  main  =  documento . querySelector ( "#main" ) ;
    const  textarea  =  main . querySelector ( `div[contenteditable="true"]` ) ;

    se  ( ! textarea )  {
        throw  new  Error ( "Não há uma conversa aberta" ) ;
    }

    para  ( const  linha  de  linhas )  {
        console . log ( linha ) ;
        textarea . foco ( ) ;
        documento . execCommand ( 'insertText' ,  false ,  linha ) ;
        textarea . dispatchEvent ( novo  Evento ( 'alterar' ,  {  bolhas : verdadeiro  } ) ) ;

        aguarde  nova  Promessa ( resolva  =>  setTimeout ( resolva ,  100 ) ) ;

        const  sendButton  =  principal . querySelector ( `[data-testid="send"]` )  ||  principal . querySelector ( `[data-icon="send"]` ) ;
        enviarBotão . clique ( ) ;

        se  ( linhas . indexOf ( linha )  !==  linhas . comprimento  -  1 )  {
            aguarde  nova  Promessa ( resolva  =>  setTimeout ( resolva ,  250 ) ) ;
        }
    }

    retornar  linhas . comprimento ;
}

enviarScript ( `
A história começou
Quando um relógio esquisito
Grudou no pulso dele vindo lá do infinito
Agora tem poderes e com eles faz bonito
É o Ben 10
(Ben 10, Ben 10, Ben 10)
Se acaso encontrá-lo, você vai admirá-lo
Diante de seus olhos ele vai se transformar
Em um ser alienígena
Que bota pra quebrar
É o Ben 10
(Ben 10)
Com seus poderes vai combater
Os inimigos e vão vencer
Ele não tem medo ou dor
Moleque muito irado
Seja onde for
É o Ben 10
` ) . then ( e  =>  console . log ( `Código finalizado, ${ e } mensagens enviadas` ) ) . pegar ( console . erro ) ;
