# Intuition
A ideia principal é encotnrar os dois números no array que somam e dão o valor da entrada de target. Como verificar todos os valores pares não é necessário, podemos otimizar isso usando um HashMap, a complexidade é de O(1) e permite buscas rápidas.

Se nums[i] faz parte da soma, o outro número que precisamos encontrar é target - nums[i]
Se já tivermos visto esse número antes, quer dizer que achamos a resposta e podemos retornar o par.

# Approach
1. Criamos um Map para armazenar os valores e seus índices (key-value pairs)
2. Percorremos o array nums para calcularmos o complemento que precisamos, se ele já estiver no Map, ele retorna os índices, caso contrário a gente armazena o índice correspondente
3. Como o problema pede que tenha apenas uma solução, sempre encontramos a resposta ser verificar a mais, logo podemos encerrar o loop.

# Complexity
- Time complexity:
O(n), Percorremos o array uma única vez e fazemos operações de inserção e busca em O(1).

- Space complexity:
O(n), No pior caso, armazenamos todos os n elementos no Map.


# Code
```typescript []
function twoSum(nums: number[], target: number): number[] {
    let numMap = new Map<number, number>();

    for (let i = 0; i < nums.length; i++) {
        let complement = target - nums[i];

        if (numMap.has(complement)) {
            return [numMap.get(complement)!, i];
        }

        numMap.set(nums[i], i);
    }

    return [];
};
```
