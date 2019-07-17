---
title: .NET 編譯器平台 (&quot;Roslyn&quot;) 擴充性 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 564201b3-1e18-4b88-b615-42c2f57f3fe8
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fba277731444a294f276f43cc67b098039f4a64f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "68204724"
---
# <a name="net-compiler-platform-quotroslynquot-extensibility"></a>.NET 編譯器平台 (&quot;Roslyn&quot;) 擴充性
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

.NET 編譯器平台 ("Roslyn") 的核心任務是開啟的 C# 和 Visual Basic 編譯器，並讓工具和開發人員共用的豐富資訊的編譯器中有關於程式。 程式碼分析工具改善程式碼品質，以及程式碼產生器協助建構應用程式。 因為工具變得越來越聰明，他們需要存取越來越多只有編譯器所擁有的深層的程式碼知識。 而不是不透明的轉譯器 （原始程式碼和出的物件程式碼），Roslyn 編譯器會提供 Api，您可以使用工具和應用程式中的程式碼相關工作。  
  
 最大好處是 Roslyn 編譯器、 其 Api、 範例和逐步解說和這些 Api 為基礎的實際工具會在的所有完整的開放原始碼[github.com/dotnet/roslyn](https://github.com/dotnet/Roslyn)。 請移至 進一步了解並開始使用 roslyn 建立與 OSS 站台。 您會發現連結，以取得最新的 C# 和 VB 功能，您可以使用做為一般使用者，以及開始運用 Roslyn Api 是工具產生器的連結。  
  
## <a name="see-also"></a>另請參閱  
 [開始使用 Roslyn 分析器](../extensibility/getting-started-with-roslyn-analyzers.md)
