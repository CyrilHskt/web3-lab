Première difficulté : Trouver le bon réseau avec le testnet d'Etherem : Sepolia. Déjà j'ai eu du mal à trouver la différence entre Sepolia, Sepolia-arbitrum et sepolia-optimism...

Puis y'a fallu trouver un faucet qui fonctionne avec Sepolia (j'ai pris celui de google https://cloud.google.com/application/web3/faucet/ethereum/sepolia).

Ensuite il a fallu suivre les instructions et jouer avec le contrat, notamment appeler await contact.info() pour avoir différents console.log qui ont amené à appeler d'autres méthodes et à la fin à chercher un mot de passe dans une variable publique du contrat.

En finalité, il a fallu appeler une des méthodes avec le mot de passe pour passer un bool à true qui a permis de déclencher la transaction qui passait le niveau.

Le code du contrat : 

```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract Instance {
    string public password;
    uint8 public infoNum = 42;
    string public theMethodName = "The method name is method7123949.";
    bool private cleared = false;

    // constructor
    constructor(string memory _password) {
        password = _password;
    }

    function info() public pure returns (string memory) {
        return "You will find what you need in info1().";
    }

    function info1() public pure returns (string memory) {
        return 'Try info2(), but with "hello" as a parameter.';
    }

    function info2(string memory param) public pure returns (string memory) {
        if (keccak256(abi.encodePacked(param)) == keccak256(abi.encodePacked("hello"))) {
            return "The property infoNum holds the number of the next info method to call.";
        }
        return "Wrong parameter.";
    }

    function info42() public pure returns (string memory) {
        return "theMethodName is the name of the next method.";
    }

    function method7123949() public pure returns (string memory) {
        return "If you know the password, submit it to authenticate().";
    }

    function authenticate(string memory passkey) public {
        if (keccak256(abi.encodePacked(passkey)) == keccak256(abi.encodePacked(password))) {
            cleared = true;
        }
    }

    function getCleared() public view returns (bool) {
        return cleared;
    }
}
```

Mais je crois que le code est incomplet, il faut aller voir sur le repo github : https://github.com/OpenZeppelin/ethernaut