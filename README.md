# Brainwallet

**Uma senha secreta → chaves de Bitcoin e Nostr.**

O **Brainwallet** é um protótipo experimental, gratuito e de código aberto (licença MIT), desenvolvido em HTML e JavaScript. Ele deriva, de forma determinística, chaves de Bitcoin e Nostr a partir de uma senha secreta fornecida pelo usuário.

> [!WARNING]
> **Não utilize este aplicativo para guardar bitcoins reais.** O projeto **não foi auditado** e não é uma carteira validada para uso financeiro. Senhas escolhidas por pessoas podem ser previsíveis e vulneráveis a ataques de dicionário e força bruta. Nunca compartilhe senhas, chaves privadas ou frases de recuperação — nem em relatórios de bugs.

## Conceito

Em carteiras Bitcoin tradicionais, normalmente é gerada uma frase de recuperação aleatória que o usuário precisa guardar. O Brainwallet explora a ideia inversa: **o usuário escolhe uma frase ou senha secreta, e o aplicativo calcula as chaves correspondentes**.

A mesma entrada, com a mesma versão do algoritmo e os mesmos parâmetros, permite reconstruir as mesmas chaves. Isso **não significa que uma senha memorizada seja tão segura quanto uma frase aleatória gerada criptograficamente**.

## Como funciona

```text
          Senha secreta escolhida pelo usuário
                         |
                      Argon2id
                         |
              Material criptográfico
                         |
             +-----------+-----------+
             |                       |
          Bitcoin                   Nostr
      Endereços e WIF           npub e nsec
             |
         BIP39 opcional
   12 ou 24 palavras derivadas
     (carteira distinta)
```

O **Argon2id** torna mais custoso testar tentativas de senha, mas **não impede** ataques contra segredos fracos. A derivação BIP39 opcional utiliza material obtido da mesma senha e cria uma carteira distinta das chaves Bitcoin derivadas diretamente e das chaves Nostr. **Essas palavras não são geradas com aleatoriedade independente.**

## Funcionalidades

- **Bitcoin:** endereços Legacy e SegWit nativo, além de chave privada WIF.
- **Nostr:** identidade pública `npub` e chave privada `nsec`.
- **BIP39 opcional:** frases determinísticas de 12 ou 24 palavras, correspondentes a uma derivação separada.
- **Interface:** 20 opções de idioma, temas claro/escuro, seções expansíveis e ocultação de dados sensíveis.
- **Código aberto:** código-fonte disponível para estudo, modificação, verificação e contribuições.

## Filosofia

1. **Simplicidade:** uma interface para explorar a derivação de chaves Bitcoin e Nostr.
2. **Autonomia:** permitir ao usuário conhecer a relação entre a senha fornecida e as chaves obtidas.
3. **Transparência:** publicar o código para inspeção independente e colaboração.

## Executar

1. Baixe o repositório usando **Code → Download ZIP**.
2. Extraia o arquivo ZIP.
3. Abra `index.html` no Google Chrome ou outro navegador moderno.

A versão atual depende de conexão à internet para carregar algumas bibliotecas criptográficas externas e a lista de palavras BIP39 em inglês. **Não é totalmente offline.** O processamento de chaves ocorre no navegador, mas essa característica, por si só, **não constitui garantia de privacidade ou segurança**.

## Limitações e segurança

- **Experimental e não auditado:** não utilizar com fundos reais.
- **Senha humana não é aleatoriedade criptográfica:** o medidor de força é apenas uma estimativa visual e não garante resistência a ataques.
- **Determinismo exige compatibilidade:** mudanças nos parâmetros ou algoritmos podem produzir chaves diferentes.
- **Dependências externas:** bibliotecas e conteúdos obtidos na internet precisam de revisão e mecanismos de integridade antes de qualquer aplicação sensível.
- **BIP39 derivado:** as palavras de recuperação não são independentes da senha original e não equivalem a uma frase gerada aleatoriamente por uma carteira tradicional.
- **Revisão pendente:** a implementação criptográfica, a compatibilidade dos endereços e o tratamento de dados sensíveis requerem testes e auditoria independente.

Se identificar um problema, abra uma *Issue*, **sem incluir senhas, seeds, chaves privadas ou informações financeiras**.

## Open source / English summary

Brainwallet is an **experimental, unaudited**, single-page HTML/JavaScript project for deterministic Bitcoin and Nostr key derivation from a user-chosen secret via Argon2id. It supports Bitcoin Legacy/SegWit addresses and WIF, Nostr npub/nsec, and optional deterministically derived 12/24-word BIP39 mnemonics **for a separate wallet**. Human-memorable secrets can be guessable; **do not use with real funds**. Some libraries and word lists require an internet connection.

## Licença

Distribuído sob a licença **MIT**. Veja [LICENSE](LICENSE).
