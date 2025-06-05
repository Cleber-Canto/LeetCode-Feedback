# Bug Report - LeetCode Feedback

### Problema: Erro no exercício "Two Sum"
**Usuário:** Cleber-Canto  
**Link do problema:** [https://leetcode.com/problems/two-sum/](https://leetcode.com/problems/two-sum/)  

## Descrição do erro:
Ao rodar o código no ambiente LeetCode, recebo o erro `ArrayIndexOutOfBoundsException`.

### Código utilizado:
```java
public class Solution {
    public int[] twoSum(int[] nums, int target) {
        // Código aqui
    }
}

---

### **4️⃣ Commitando as Mudanças**
✅ Após finalizar o arquivo, **role a tela para baixo**.  
✅ No campo **"Commit changes"**, escreva uma breve descrição, como `"Adicionando bug report Two Sum"`.  
✅ Clique em **"Commit new file"** para enviar a alteração.  

---

### **5️⃣ Criando um Pull Request (Opcional)**
📌 Se quiser **sugerir alterações** ao projeto, **crie um Pull Request**:  
✅ Vá para a aba **"Pull requests"**.  
✅ Clique em **"New pull request"**.  
✅ Compare as mudanças e clique em **"Create pull request"**.  
✅ Preencha um comentário explicando sua sugestão e envie!  

---

🚀 **Agora sua contribuição foi adicionada ao repositório!** Quer que eu te ajude com mais detalhes sobre GitHub? 😃
class Solution {
    public double findMedianSortedArrays(int[] nums1, int[] nums2) {
        // Garantir que nums1 seja o menor array
        if (nums1.length > nums2.length) {
            return findMedianSortedArrays(nums2, nums1);
        }
        
        int x = nums1.length;
        int y = nums2.length;
        int low = 0, high = x;
        
        while (low <= high) {
            int partitionX = (low + high) / 2;
            int partitionY = (x + y + 1) / 2 - partitionX;

            int maxLeftX = (partitionX == 0) ? Integer.MIN_VALUE : nums1[partitionX - 1];
            int minRightX = (partitionX == x) ? Integer.MAX_VALUE : nums1[partitionX];

            int maxLeftY = (partitionY == 0) ? Integer.MIN_VALUE : nums2[partitionY - 1];
            int minRightY = (partitionY == y) ? Integer.MAX_VALUE : nums2[partitionY];

            if (maxLeftX <= minRightY && maxLeftY <= minRightX) {
                if ((x + y) % 2 == 0) {
                    return (Math.max(maxLeftX, maxLeftY) + Math.min(minRightX, minRightY)) / 2.0;
                } else {
                    return Math.max(maxLeftX, maxLeftY);
                }
            } else if (maxLeftX > minRightY) {
                high = partitionX - 1;
            } else {
                low = partitionX + 1;
            }
        }

        throw new IllegalArgumentException("Os arrays de entrada não estão ordenados corretamente.");
    }
}
