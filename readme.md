## Motivação


Em jogos ou aplicações que envolvem a criação de múltiplas instâncias de entidades (como inimigos, NPCs, ou objetos reutilizáveis), criar novos objetos repetidamente pode ser ineficiente. Resultando no consumo excessivo de memória: Se cada entidade fosse criada individualmente sem reuso, o sistema alocaria mais memória desnecessariamente.

 Sempre que fosse necessário criar um monstro, seria preciso instanciar manualmente e definir seus atributos.
Dificuldade de manutenção: Caso fosse necessário modificar a criação de entidades (por exemplo, adicionar novos atributos padrão), seria necessário alterar o código em vários locais.

Para Solucionar esse problema
A implementação do Factory Pattern com Flyweight resolve esses problemas:

Reutilização de Objetos: O código reutiliza entidades com base no identificador prefab, evitando alocações desnecessárias.
Facilidade de Manutenção: Toda a lógica de criação de entidades fica centralizada na EntityFactory, tornando modificações futuras mais fáceis.
Escalabilidade: Com o método bulkCreateMonster, múltiplas entidades podem ser criadas dinamicamente sem precisar instanciar cada uma manualmente.

@startuml

class EntityFactory {
    - entites: Map<String, Monster>
    + createMonster(prefab: String, name: String, health: int, damage: int): Monster
    + bulkCreateMonster(prefab: String, name: String, health: int, damage: int, quantity: int): void
}

class Monster {
    + prefab: String
    + name: String
    + health: int
    + damage: int
    + details(): void
}

EntityFactory "1" -- "*" Monster : creates
@enduml@startuml

class EntityFactory {
    - entites: Map<String, Monster>
    + createMonster(prefab: String, name: String, health: int, damage: int): Monster
    + bulkCreateMonster(prefab: String, name: String, health: int, damage: int, quantity: int): void
}

class Monster {
    + prefab: String
    + name: String
    + health: int
    + damage: int
    + details(): void
}

EntityFactory "1" -- "*" Monster : creates
@enduml


```js




```