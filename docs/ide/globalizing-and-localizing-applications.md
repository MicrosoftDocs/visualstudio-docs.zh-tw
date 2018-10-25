---
title: 全球化和當地語系化應用程式
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- globalization [Visual Studio]
- Visual Basic code, international applications
- C#, international applications
- localization [Visual Studio]
- world-ready applications
- international applications [Visual Studio]
ms.assetid: 4d9815ae-3e80-4b4d-933d-f8309aee18d5
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 73e638b2474342987963c02f442f5d7a98a6e44e
ms.sourcegitcommit: b6dfa1bdf4c23c2e341754454bbd4758db2218e0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/08/2018
ms.locfileid: "48863592"
---
# <a name="globalizing-and-localizing-applications"></a>全球化和當地語系化應用程式

如果您打算將應用程式散發給國際適用對象，您必須在設計和開發階段期間牢記下列幾項重點。 即使您不打算這麼做，這個簡單的前置工作，可讓您在未來版本的應用程式計劃有所變更時，更加事半功倍。 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 的內建服務可讓您使用 Visual Studio 的 Managed 開發功能，輕鬆開發單一應用程式，使其適應不同的地區設定。

## <a name="resources"></a>資源

 Visual Studio 在設計之初就已設想到利用 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 內建的服務優勢，讓針對國際適用對象的開發作業更加輕鬆。 下列文章有助您了解 Visual Studio 內建的國際化功能。

 [以 .NET Framework 為基礎的國際應用程式簡介](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md)：介紹使用 Visual Studio 和 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 開發國際市場軟體的相關基本概念。

 [當地語系化應用程式](../ide/localizing-applications.md)：提供針對特定文化特性自訂應用程式的相關頁面連結。

 [全球化應用程式](../ide/globalizing-applications.md)：提供建立支援多種文化特性應用程式的相關頁面連結。

## <a name="see-also"></a>另請參閱

- [開發世界性的應用程式的最佳做法](/dotnet/standard/globalization-localization/best-practices-for-developing-world-ready-apps)提供適用於國際對象的程式設計相關資訊。
- [類別庫概觀](/dotnet/standard/class-library-overview)介紹類別、介面和實值型別，以加速和最佳化開發過程並提供對系統功能的存取。
- <xref:System.Globalization> 顯示此命名空間內的類別，其定義與文化特性相關的資訊，包括語言、國家/地區、使用中的行事曆、日期、貨幣和數字的格式模式，以及字串的排序順序。
- <xref:System.Resources> 顯示此命名空間內的類別和介面，其可讓開發人員建立、儲存和管理應用程式中所使用的各種文化特性相關資源。