---
title: 以 .NET Framework 為基礎的國際應用程式簡介
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- strings [Visual Studio], localizing
- Web applications [.NET Framework], globalization
- Windows Forms, globalization
- localization [Visual Studio], culture setting
- fallback resources
- culture, setting
- globalization [Visual Studio], culture setting
- resources [Visual Studio], localization
- localization [Visual Studio], .NET localization model
- Assembly Resource file template
- resources [Visual Studio], fallback system
- international applications [Visual Studio], about international applications
- globalization [Visual Studio], international applications
- ASP.NET, globalization
- resource files, fallback processes
- user interface, culture setting
ms.assetid: b0788993-e62d-4f68-8235-5f87b1d48525
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 773e6a2f351c0256fee17b1e07ff37fe9567198b
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="introduction-to-international-applications-based-on-the-net-framework"></a>以 .NET Framework 為基礎的國際應用程式簡介

在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中，建立世界性的應用程式有兩個部分︰全球化，設計適用不同文化特性應用程式的程序；當地語系化，轉譯特定文化特性資源的程序。 如需針對國際市場使用者設計應用程式的一般資訊，請參閱[開發世界性的應用程式的最佳做法](http://msdn.microsoft.com/Library/f08169c7-aad8-4ec3-9a21-9ebd3b89986c)。

 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 當地語系化模型包含主要組件，它包含應用程式程式碼和後援資源：最初開發應用程式所用語言的字串、影像和其他物件。 每個已當地語系化的應用程式都有附屬組件，或只包含當地語系化資源的組件。 因為主要組件一律包含後援資源，所以如果在當地語系化的附屬組件中找不到資源，<xref:System.Resources.ResourceManager> 就會以階層方式嘗試載入資源，最後回到主要組件的資源。 [階層式組織當地語系化的資源](../ide/hierarchical-organization-of-resources-for-localization.md)中會詳細說明資源後援系統。

 您應該考慮使用的一項當地語系化資源，是適用所有 Microsoft 當地語系化產品的詞彙。 這個 CSV 檔案包含超過 12,000 個英文詞彙，以及多達 59 種不同語言的翻譯。 詞彙可在 [Microsoft Terminology Translations](http://go.microsoft.com/fwlink/?LinkId=128146) 網頁下載。

 Windows Forms 應用程式的專案系統可為後援和每個必要的額外 UI 文化特性產生資源檔。 後援資源檔內建在主要組件中，而特定文化特性資源檔則內建在附屬組件中，各 UI 文化特性一個。 當您建置專案時，資源檔會從 Visual Studio XML 格式 (.resx) 編譯為中繼二進位格式 (.resources)，然後內嵌在附屬組件中。

 Windows Forms 和 Web Forms 的專案系統都可讓您使用組件資源檔範本建置資源檔、存取資源，以及建置專案。 附屬組件會和主要組件一起建立。

 執行當地語系化的應用程式時，其外觀是由兩個文化特性值決定。 (「文化特性」是一組與使用者的語言、環境及文化慣例相關的使用者喜好設定資訊。)UI 文化特性設定會決定載入的資源。 UI 文化特性 (Culture) 在 Web.config 檔案和網頁指示詞中設定為 `UICulture`，在 Visual Basic 或 C# 程式碼中設定為 <xref:System.Globalization.CultureInfo.CurrentUICulture%2A>。 文化特性設定決定日期、數字、貨幣等值的格式。 文化特性在 Web.config 檔案和網頁指示詞中設定為 `Culture`，在 Visual Basic 或 C# 程式碼中設定為 <xref:System.Globalization.CultureInfo.CurrentCulture%2A>。

## <a name="see-also"></a>另請參閱

- <xref:System.Globalization>
- <xref:System.Resources>
- [全球化和當地語系化應用程式](../ide/globalizing-and-localizing-applications.md)
- [安全性和當地語系化附屬組件](../ide/security-and-localized-satellite-assemblies.md)