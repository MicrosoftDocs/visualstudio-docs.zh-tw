---
title: 當地語系化工具
description: 瞭解 Visual Studio 中包含的當地語系化工具，以及如何使用這些工具以多種語言建立當地語系化的應用程式。
ms.custom: SEO-VS-2020
ms.date: 02/15/2019
ms.topic: reference
helpviewer_keywords:
- globalization [Visual Studio]
- Visual Basic code, international applications
- C#, international applications
- localization [Visual Studio]
- world-ready applications
- international applications [Visual Studio]
ms.assetid: 4d9815ae-3e80-4b4d-933d-f8309aee18d5
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 77402f7503818b310a592a39706ac717ac728852
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99847956"
---
# <a name="develop-globalized-and-localized-apps"></a>開發全球化和當地語系化應用程式

Visual Studio 利用 [.NET](/dotnet/standard/globalization-localization/) 所內建的服務，讓針對國際適用對象的開發作業變得更加輕鬆。

例如，Windows Forms 應用程式的專案系統可同時為後援和其他每個 UI 文化特性產生資源檔。 當您在 Visual Studio 中建置專案時，資源檔會從 Visual Studio XML 格式 (.resx) 編譯為中繼二進位格式 (.resources)，然後內嵌在附屬組件中。 如需詳細資訊，請參閱 [Visual Studio 中的資源檔](/dotnet/framework/resources/creating-resource-files-for-desktop-apps#VSResFiles)及 [Create satellite assemblies for desktop apps](/dotnet/framework/resources/creating-satellite-assemblies-for-desktop-apps) (建立傳統型應用程式的附屬組件)。

## <a name="bidirectional-languages"></a>雙向語言

您可以使用 Visual Studio 來建立應用程式，以正確顯示由右至左撰寫的語言文字，包括阿拉伯文和希伯來文。 針對某些功能，您可以直接設定屬性， 若為其他情況，則必須在程式碼中實作功能。

> [!NOTE]
> 若要輸入及顯示雙向語言，您必須使用已設定適當語言的 Windows 版本。 這包括已安裝適當語言套件的英文版 Windows，或正確的 Windows 當地語系化版本。

### <a name="apps-that-support-bidirectional-languages"></a>支援雙向語言的應用程式

- Windows 應用程式

   您可以建立完整的雙向應用程式，以支援雙向文字、由右至左讀取順序及鏡像功能 (將視窗、功能表、對話方塊等配置反轉)。 除了鏡像功能以外，這些功能皆為預設提供或以屬性設定形式提供。 某些功能 (例如訊息方塊) 本身就支援鏡像， 但若為其他情況，則必須在程式碼中實作鏡像。 如需詳細資訊，請參閱 [Windows Forms 應用程式的雙向支援](/dotnet/framework/winforms/advanced/bi-directional-support-for-windows-forms-applications)。

- Web 應用程式

   Web 服務支援 UTF-8 和 Unicode 文字的接收與傳送作業，因此非常適合使用雙向語言的應用程式。 Web 用戶端應用程式需仰賴瀏覽器來呈現其使用者介面；因此，Web 應用程式的雙向支援程度與使用者瀏覽器對這些雙向功能的支援程度相關。 在 Visual Studio 中，您可以建立支援阿拉伯文或希伯來文文字、由右至左的讀取順序、檔案編碼方式及當地文化特性設定的應用程式。 如需詳細資訊，請參閱 [ASP.NET web 應用程式的雙向支援](/previous-versions/6eedwbtt(v=vs.140))。

> [!NOTE]
> 主控台應用程式不支援雙向語言的文字。 這是搭配使用 Windows 與主控台應用程式產生的後果。

## <a name="see-also"></a>另請參閱

- [Visual Studio 中的雙向語言支援](use-bidirectional-languages.md)
- [將 .NET 應用程式全球化和當地語系化](/dotnet/standard/globalization-localization/)
- [.NET 應用程式中的資源](/dotnet/framework/resources/)