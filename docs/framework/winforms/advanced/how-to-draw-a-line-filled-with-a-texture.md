---
title: 'Como: desenhar uma linha preenchida com uma textura'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drawing [Windows Forms], lines
- lines [Windows Forms], texture
- drawing lines [Windows Forms], texture
ms.assetid: dc9118cc-f3c2-42e5-8173-f46d41d18fd5
ms.openlocfilehash: c0f90c298f48aeb96893bb09241faddc08d8a49d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62004271"
---
# <a name="how-to-draw-a-line-filled-with-a-texture"></a>Como: desenhar uma linha preenchida com uma textura
Em vez de desenhar uma linha com uma cor sólida, você pode desenhar uma linha com uma textura. Para desenhar linhas e curvas com uma textura, crie uma <xref:System.Drawing.TextureBrush> do objeto e passá-lo <xref:System.Drawing.TextureBrush> do objeto para um <xref:System.Drawing.Pen.%23ctor%2A> construtor. O bitmap associado ao pincel de textura é usado para organizar lado a lado o plano (modo invisível) e quando a caneta desenha uma linha ou curva, o traço de caneta revela determinados pixels da textura lado a lado.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir cria uma <xref:System.Drawing.Bitmap> objeto do arquivo `Texture1.jpg`. Esse bitmap é usado para construir um <xref:System.Drawing.TextureBrush> objeto e o <xref:System.Drawing.TextureBrush> objeto é usado para construir um <xref:System.Drawing.Pen> objeto. A chamada para <xref:System.Drawing.Graphics.DrawImage%2A> desenha o bitmap com seu canto superior esquerdo em (0, 0). A chamada para <xref:System.Drawing.Graphics.DrawEllipse%2A> usa o <xref:System.Drawing.Pen> objeto ao desenhar uma elipse texturizada.  
  
 A ilustração a seguir mostra o bitmap e a elipse texturizada:  
  
 ![Captura de tela que mostra o bitmap e a elipse texturizada.](./media/how-to-draw-a-line-filled-with-a-texture/bitmap-textured-ellipse.png)  
  
 [!code-csharp[System.Drawing.UsingAPen#61](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.UsingAPen#61](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#61)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Criar um formulário do Windows e lidar com o formulário <xref:System.Windows.Forms.Control.Paint> eventos. Cole o código anterior para o <xref:System.Windows.Forms.Control.Paint> manipulador de eventos. Substitua `Texture.jpg` por uma imagem válida no sistema.  
  
## <a name="see-also"></a>Consulte também

- [Usando uma caneta para desenhar linhas e formas](using-a-pen-to-draw-lines-and-shapes.md)
- [Elementos Gráficos e Desenho nos Windows Forms](graphics-and-drawing-in-windows-forms.md)
