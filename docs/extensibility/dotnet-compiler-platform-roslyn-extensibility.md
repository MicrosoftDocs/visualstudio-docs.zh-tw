---
title: .NET 編譯器平台 (&quot;Roslyn&quot;) 擴充性 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 564201b3-1e18-4b88-b615-42c2f57f3fe8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 09287c48285bfcdc32b1a7d558d44f9d212f1b41
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31126932"
---
# <a name="net-compiler-platform-quotroslynquot-extensibility"></a>.NET 編譯器平台 (&quot;Roslyn&quot;) 擴充性
核心任務.NET 編譯器平台 ("Roslyn") 是開啟的 C# 和 Visual Basic 編譯器，並讓工具和共用的豐富資訊編譯器中的開發人員需要的程式相關。 程式碼分析工具可改善程式碼品質和程式碼產生器應用程式建構中的輔助工具。 工具取得更佳，因為它們需要的存取為越來越多的唯一編譯器擁有深層的程式碼知識。 而不是不透明的轉譯器 （來源中的程式碼和物件的程式碼時），Roslyn 編譯器會提供 Api，您可以使用的工具和應用程式中的程式碼相關的工作。  
  
 最棒的是 Roslyn 編譯器、 其應用程式開發介面、 範例和逐步解說和這些 Api 上層所建立的真實工具在的所有完整的開放原始碼[github.com/dotnet/roslyn](https://github.com/dotnet/Roslyn)。 請移至 進一步了解並開始使用 Roslyn 的 OSS 站台。 您會發現連結，以取得最新的 C# 和 VB 功能可讓您以一般使用者，以及若要開始為利用 Roslyn Api 的工具產生器的連結。  
  
## <a name="see-also"></a>另請參閱  
 [開始使用 Roslyn 分析器](../extensibility/getting-started-with-roslyn-analyzers.md)