---
title: Como associar a um serviço Web
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binding data [WPF], Web service
- Web service binding [WPF]
- data binding [WPF], Web service
ms.assetid: 77e2d373-69ba-4cbd-b6f5-2c83c38fc98b
ms.openlocfilehash: 3a3f6edc974448ddab9fe30e97bdc1130d3b97dc
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449966"
---
# <a name="how-to-bind-to-a-web-service"></a>Como associar a um serviço Web
Este exemplo mostra como associar a objetos retornados por chamadas de método de serviço Web.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o serviço de conteúdo do MTPS (sistema de publicação do MSDN/TechNet) para recuperar a lista de idiomas com suporte em um documento especificado.  
  
 Antes de chamar um serviço Web, é necessário criar uma referência a ele. Para criar uma referência Web para o serviço MTPS usando o Visual Studio, siga as seguintes etapas:  
  
1. Abra o projeto no Visual Studio.  
  
2. No menu **Projeto**, clique em **Adicionar referência Web**.  
  
3. Na caixa de diálogo, defina a **URL** como [http://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl](https://services.msdn.microsoft.com/contentservices/contentservice.asmx?wsdl).  
  
4. Pressione **Ir** e, em seguida, **Adicionar referência**.  
  
 Em seguida, você chama o método de serviço Web e define a <xref:System.Windows.FrameworkElement.DataContext%2A> do controle ou da janela apropriada para o objeto retornado. O método `GetContent` do serviço MTPS usa uma referência ao objeto `getContentRequest`. Portanto, o exemplo a seguir primeiro define um objeto de solicitação:  
  
 [!code-csharp[BindToWebService#Namespace](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml.cs#namespace)]
 [!code-vb[BindToWebService#Namespace](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BindToWebService/VisualBasic/Window1.xaml.vb#namespace)]  
[!code-csharp[BindToWebService#WebServiceCall](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml.cs#webservicecall)]
[!code-vb[BindToWebService#WebServiceCall](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BindToWebService/VisualBasic/Window1.xaml.vb#webservicecall)]  
  
 Depois que o <xref:System.Windows.FrameworkElement.DataContext%2A> tiver sido definido, você poderá criar associações para as propriedades do objeto ao qual o <xref:System.Windows.FrameworkElement.DataContext%2A> foi definido. Neste exemplo, o <xref:System.Windows.FrameworkElement.DataContext%2A> é definido como o objeto `getContentResponse` retornado pelo método `GetContent`. No exemplo a seguir, o <xref:System.Windows.Controls.ItemsControl> é associado a e exibe os valores de `locale` de `availableVersionsAndLocales` de `getContentResponse`.  
  
 [!code-xaml[BindToWebService#Binding](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToWebService/CSharp/Window1.xaml#binding)]  
  
 Para obter informações sobre a estrutura de `getContentResponse`, consulte [documentação do serviço de conteúdo](https://services.msdn.microsoft.com/ContentServices/ContentService.asmx).  
  
## <a name="see-also"></a>Confira também

- [Visão geral da vinculação de dados](../../../desktop-wpf/data/data-binding-overview.md)
- [Visão geral das origens da associação](binding-sources-overview.md)
- [Disponibilizar dados para associação em XAML](how-to-make-data-available-for-binding-in-xaml.md)
