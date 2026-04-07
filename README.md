# Protocolo Web3 

Guia direto para rodar o projeto e testar pelo frontend.

## 1) Preencher o `.env`

1. Crie o arquivo `.env` na raiz do projeto (ou copie de `.env.example`).
2. Preencha os campos:

```bash
SEPOLIA_RPC_URL=https://seu-rpc-sepolia
PRIVATE_KEY=0xSUA_CHAVE_PRIVADA_DA_CARTEIRA_DE_TESTE
VOTING_PERIOD_BLOCKS=5
```

Regras importantes:
- Use carteira de teste (nunca carteira principal).
- Garanta ETH de teste em Sepolia nessa carteira (faucet).

## 2) Instalar dependências e fazer deploy

No terminal, na raiz do projeto:

```bash
npm install
npx hardhat compile
npx hardhat run scripts/deploy.js --network sepolia
```

Esse deploy gera/atualiza `deployment.json` com os endereços dos contratos.

## 3) Ativar backend e frontend

Use dois terminais.

Terminal 1 Backend:

```bash
npm run backend
```

Backend disponível em `http://127.0.0.1:8787`.

Terminal 2 Frontend:

```bash
npx serve frontend
```

Frontend disponível em `http://localhost:3000`.

Ao abrir a página:
- O frontend tenta carregar automaticamente os contratos via `deployment.json`/backend.
- Clique em **Conectar carteira** e aceite trocar para a rede **Sepolia** no MetaMask.

## 4) Passo a passo para testar as features no frontend

## 4.1 Conexão e DAO
1. Clique **Conectar carteira**.
2. Clique **Delegar votos**.

## 4.2 Staking
1. Defina a quantidade em `Quantidade PGT`.
2. Clique **Aprovar**.
3. Clique **Stake**.
4. Aguarde alguns blocos.
5. Clique **Resgatar recompensa**.

## 4.3 NFT
1. Clique **Ver balance NFT** para consultar quantos NFTs sua carteira possui.
2. O mint é executado via governança, não é mint direto no frontend.

## 4.4 Governança
1. Em **Descrição da proposta**, escreva o texto.
2. Em **Target**, use o endereço do `ProtocolNFT`, normalmente já preenchido.
3. Em **Calldata**, informe os bytes da função a executar.
4. Clique **Criar proposta**.
5. Informe o ID da proposta em `ID da proposta`.
6. Clique **Votar a favor**.
7. Após o fim do período de votação, clique **Executar** após o prazo.

