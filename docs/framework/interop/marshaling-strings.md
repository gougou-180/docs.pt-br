---
title: Realizando marshaling de cadeias de caracteres
ms.date: 03/30/2017
helpviewer_keywords:
- marshaling, samples
- platform invoke, marshaling data
- data marshaling, strings
- data marshaling, samples
- data marshaling, platform invoke
- marshaling. strings
- marshaling, platform invoke
- sample applications [.NET Framework], marshaling strings
ms.assetid: e21b078b-70fb-4905-be26-c097ab2433ff
ms.openlocfilehash: 88b6342038f99bf06fa2986c43f422e63cffd31e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124375"
---
# <a name="marshaling-strings"></a>Realizando marshaling de cadeias de caracteres
A invocação de plataforma copia parâmetros de cadeia de caracteres, convertendo-os do formato do .NET Framework (Unicode) para o formato não gerenciado (ANSI), se necessário. Já que as cadeias de caracteres gerenciadas são imutáveis, a invocação de plataforma não as copia de volta da memória não gerenciada para a memória gerenciada quando a função retorna.  
  
 A tabela a seguir lista as opções de marshaling para cadeias de caracteres, descreve o uso delas e fornece um link para a amostra de .NET Framework correspondente.  
  
|Cadeia de Caracteres|Descrição|Amostra|  
|------------|-----------------|------------|  
|Por valor.|Passa cadeias de caracteres como parâmetros In.|[MsgBox](msgbox-sample.md)|  
|Como resultado.|Retorna cadeias de caracteres de código não gerenciado.|[Cadeias de Caracteres](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e765dyyy(v=vs.100))|  
|Por referência.|Passa cadeias de caracteres como parâmetros In/Out usando <xref:System.Text.StringBuilder>.|[Buffers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/x3txb6xc(v=vs.100))|  
|Em uma estrutura por valor.|Passa cadeias de caracteres em uma estrutura que é um parâmetro In.|[Structs](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/eadtsekz(v=vs.100))|  
|Em uma estrutura por referência **(char\*)** .|Passa cadeias de caracteres em uma estrutura que é um parâmetro In/Out. A função não gerenciada espera um ponteiro para um buffer de caracteres e o tamanho do buffer é um membro da estrutura.|[Cadeias de Caracteres](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e765dyyy(v=vs.100))|  
|Em uma estrutura por referência **(char[])** .|Passa cadeias de caracteres em uma estrutura que é um parâmetro In/Out. A função não gerenciada espera um buffer de caracteres inserido.|[OSInfo](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/795sy883(v=vs.100))|  
|Em uma classe por valor **(char\*)** .|Passa cadeias de caracteres em uma classe (uma classe é um parâmetro In/Out). A função não gerenciada espera um ponteiro para um buffer de caracteres.|[OpenFileDlg](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w5tyztk9(v=vs.100))|  
|Em uma classe por valor **(char[])** .|Passa cadeias de caracteres em uma classe (uma classe é um parâmetro In/Out). A função não gerenciada espera um buffer de caracteres inserido.|[OSInfo](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/795sy883(v=vs.100))|  
|Como uma matriz de cadeias de caracteres por valor.|Cria uma matriz de cadeias de caracteres que é passada por valor.|[Matrizes](marshaling-different-types-of-arrays.md)|  
|Como uma matriz de estruturas que contêm cadeias de caracteres por valor.|Cria uma matriz de estruturas que contêm cadeias de caracteres e a matriz é transmitida por valor.|[Matrizes](marshaling-different-types-of-arrays.md)|  
  
## <a name="see-also"></a>Consulte também

- [Marshaling padrão para cadeias de caracteres](default-marshaling-for-strings.md)
- [Marshaling de dados com a invocação de plataforma](marshaling-data-with-platform-invoke.md)
- [Marshaling de classes, estruturas e uniões](marshaling-classes-structures-and-unions.md)
- [Marshaling de diversos tipos de matrizes](marshaling-different-types-of-arrays.md)
- [Exemplos diversos de marshaling](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ss9sb93t(v=vs.100))
