---
title: 'Como: Ocultar ToolStripMenuItems'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], hiding
- MenuStrip control [Windows Forms], hiding menu items
- menus [Windows Forms], hiding menu items
- menu items [Windows Forms], hiding
- hiding menu items
ms.assetid: 418a768f-808a-44cd-8cef-f4e161883621
ms.openlocfilehash: 64c0f093063357c1e8db5933c035cc8295ad4f1e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64623048"
---
# <a name="how-to-hide-toolstripmenuitems"></a>Como: Ocultar ToolStripMenuItems
Ocultando itens de menu é uma maneira de controlar a interface do usuário do seu aplicativo e restringir comandos do usuário. Geralmente, é recomendável ocultar um menu inteiro quando todos os itens de menu estão indisponíveis. Isso apresenta menos distrações para o usuário. Além disso, pode ser útil ocultar e desabilitar o menu ou item de menu, visto que apenas ocultar não impede que o usuário acesse um comando de menu usando uma tecla de atalho.  
  
### <a name="to-hide-any-menu-item-programmatically"></a>Para ocultar qualquer item de menu de forma programática  
  
- Dentro do método em que você definir as propriedades do item de menu, adicionar código para definir a <xref:System.Windows.Forms.ToolStripItem.Visible%2A> propriedade para `false`.  
  
    ```vb  
    MenuItem3.Visible = False  
    ```  
  
    ```csharp  
    menuItem3.Visible = false;  
    ```  
  
    ```cpp  
    menuItem3->Visible = false;  
    ```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Forms.ToolStripItem.Visible%2A>
- <xref:System.Windows.Forms.MenuStrip>
- [Visão geral do controle MenuStrip](menustrip-control-overview-windows-forms.md)
- [Como: Desabilitar ToolStripMenuItems](how-to-disable-toolstripmenuitems.md)
