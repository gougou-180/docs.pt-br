---
title: Elimine elementos duplicados de uma sequência
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2b224a84-bad5-4843-adcc-14e784d280f5
ms.openlocfilehash: 9b8e19ac76869c33d01a59ee3aad104a7ddbb8f7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782215"
---
# <a name="eliminate-duplicate-elements-from-a-sequence"></a>Elimine elementos duplicados de uma sequência
Use o operador de <xref:System.Linq.Queryable.Distinct%2A> para eliminar os elementos duplicados de uma sequência.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa <xref:System.Linq.Queryable.Distinct%2A> para selecionar uma sequência de cidades exclusivos que têm clientes.  
  
 [!code-csharp[DLinqQueryExamples#36](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#36)]
 [!code-vb[DLinqQueryExamples#36](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#36)]  
  
## <a name="see-also"></a>Consulte também

- [Exemplos de consulta](query-examples.md)
