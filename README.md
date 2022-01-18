# Instituto InfNet - PGPJAV01C1-3N-P1 - Serviços em Nuvem - 2021/2




#### Prova Professor Leonardo Silva da Gloria
#### Grupo: Eduardo Gaspar, Paulo Gurjão, William dos Santos Pereira<br><br>


## Projeto de Bloco - Jogo RPG com Arquitetura em  Microserviços 

O objetivo é projetar e implementar os serviços REST de um jogo de RPG baseado em turnos.<br><br>

## Serviços a Serem Implementados pelo Grupo

- [/log](#log) - Este repositório
- [/heroi](https://github.com/pgurjao/heroi-gen#heroi)
- [/ranking]()

Veja o <b>`swagger`</b> desses serviços [aqui](https://github.com/pgurjao/heroi-gen/blob/master/src/main/resources/swagger/swaggerHeroi-Gen.yaml). Cole o conteúdo do swagger em [editor.swagger.io](https://editor.swagger.io/) para ver com a formatação.

<h2 id="log">Microserviço /log</h2>

Recebe o resultado de cada turno da partida (quem sofreu quantos pontos de dano, etc) e salva de modo permitir o seu "replay", se necessário. Também permite ao microserviço `/ranking` fazer o cálculo da pontuação ao final da partida. É chamado via `POST` e o body deve conter:

```json
{
  "idBatalha": "identificador único da batalha na DB",
  "usuario": "nome do usuário no sistema",
  "heroi": "tipo de herói (GUERREIRO, BARBARO, PALADINO)",
  "monstro": "tipo de monstro (MORTO_VIVO, ORC, KOBOLD)",
  "iniciativa": "tipo do personagem que está atacando (GUERREIRO, ORC, etc)",
  "dano": "Integer (dano efetivamente causado ao personagem)"
}
```

Exemplo:

```json
{
  "idBatalha": "123456",
  "usuario": "Bruninha Destruidora",
  "heroi": "BARBARO",
  "monstro": "ORC",
  "iniciativa": "ORC",
  "dano": 4
}
```


## Critérios de Avalição (pontuação aproximada atiginda até o momento: 3.5)

- [x] 1. ~~Implementar os serviços seguindo os padrões restfull: 2 pontos~~
- [x] 2. ~~Receber configurações do servidor de configuração: 0.5 ponto~~
- [ ] 3. Decodificar o Token JWT enviado para saber qual usuário está jogando: 0.5 ponto **(Pedro)** <br>
**Obs.: Se o seu MS não precisar saber qual o usuário está jogando o tópico 2 passa a valer 1 ponto** <br>

- [ ] 4. Se registrar no Eureka: 1 ponto **(Paulo)**
- [ ] 5. Utilizar ClientSide Loadbalancer (Ribbon ou Feign): 1 ponto
- [ ] 6. Ser resiliente a falhas: 1 a 2 pontos<br>
**Obs.: 1 ponto = Implementar apenas um método visto, 2 pontos = implementar mais de 1** <br>

- [ ] 7. Criar uma conta no Papertrail e utilizar agregação de Logs: 0.5 ponto **(William)**
- [ ] 8. Utilizar Zipkin: 0.5 ponto
- [ ] 9. Utilizar algum tipo de Cache: 0.5 ponto<br>
**Obs.: Se o serviço implementado não possuir a necessidade de cache o Zipkin passa a valer 1 ponto. O aluno deverá explicar por que o cache não se faz necessário** <br>

- [x] 10. ~~Colocar os códigos em repositório público e com README: 0.5 ponto~~
- [x] 11. ~~Utilizar swagger para documentar o serviço: 1 ponto~~
