---
title: 使用雙向語言建立應用程式 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Hebrew character display, creating applications
- bi-directional language support, about bi-directional language support
- Arabic language, creating applications
ms.assetid: b56f9795-ed8d-4452-9d49-8ca0b0145d86
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 9aabfa2573ead0adb8db80a3a2fbeb76e5cd7b5b
ms.sourcegitcommit: 29ef88fc7d1511f05e32e9c6e7433e184514330d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="creating-applications-in-bi-directional-languages"></a>使用雙向語言建立應用程式
您可以使用 Visual Studio 來建立應用程式，以正確顯示由右至左撰寫的語言文字，包括阿拉伯文和希伯來文。 針對某些功能，您可以直接設定屬性， 若為其他情況，則必須在程式碼中實作功能。  
  
> [!NOTE]
>  若要輸入及顯示雙向語言，您必須使用已設為適當語言的 Windows 版本。 這包括已安裝適當語言套件的英文版 Windows，或正確的 Windows 當地語系化版本。  
  
## <a name="types-of-application-that-support-bi-directional-languages"></a>支援雙向語言的應用程式類型  
  
-  Windows 應用程式： 您可以建立完整的雙向應用程式，以支援雙向文字、由右至左讀取順序及鏡像功能 (將視窗、功能表、對話方塊等配置反轉)。 除了鏡像功能以外，這些功能皆為預設提供或以屬性設定形式提供。 某些功能 (例如訊息方塊) 本身就支援鏡像， 但若為其他情況，則必須在程式碼中實作鏡像。 如需詳細資訊，請參閱 [Windows Forms 應用程式的雙向支援](http://msdn.microsoft.com/Library/7b622fa4-f390-4e4d-b624-83a1917cccf2)。  
  
-  Web 應用程式： Web 服務可支援 UTF-8 和 Unicode 文字的接收與傳送作業，因此非常適合使用雙向語言的應用程式。 Web 用戶端應用程式的使用者介面需仰賴瀏覽器，因此，Web 應用程式的雙向支援程度與使用者瀏覽器對這些雙向功能的支援程度息息相關。 在 Visual Studio 中，您可以建立支援阿拉伯文或希伯來文文字、由右至左的讀取順序、檔案編碼方式及當地文化特性設定的應用程式。 如需詳細資訊，請參閱 [ASP.NET Web 應用程式的雙向支援](http://msdn.microsoft.com/Library/5576f9b1-9b86-41ef-8354-092d366bcd03)。  
  
-  主控台應用程式 主控台應用程式不支援雙向語言的文字。 這是搭配使用 Windows 與主控台應用程式產生的後果。  
  
## <a name="visual-studio-features-that-are-fully-supported"></a>完全支援的 Visual Studio 功能  
 在 Visual Studio 的設計階段中，您可以透過下列方式來使用雙向語言：  
  
-   **文字輸入**：Visual Studio 可支援 Unicode，因此如果您的系統已設好適當的地區設定和輸入語言，即可使用阿拉伯文或希伯來文輸入文字。 (阿拉伯文支援包括 Kashida 和讀音符號)。  
  
-   **物件名稱**：您可以使用雙向語言，將名稱指派給方案、專案、檔案、資料夾等等。 在程式碼中，您可以針對變數、類別、物件、屬性、中繼資料以及其他項目的名稱使用雙向語言。  
  
-   **檔案編碼方式**：您可以使用特定語言或 Unicode 編碼方式，儲存及開啟檔案。 如需詳細資訊，請參閱[如何：使用編碼來儲存及開啟檔案](../ide/how-to-save-and-open-files-with-encoding.md)。  
  
## <a name="features-with-limited-or-no-support"></a>有限支援或不支援的功能  
 Visual Studio 並非全數支援雙向語言應用程式通用的其他功能；在某些情況下，甚至完全不支援。 它們包括：  
  
**由右至左的讀取順序**：您在 Visual Studio 中使用的文字輸入控制項，預設會採用由左至右的讀取順序。 在大部分情況下，您可以使用標準 Windows 筆勢來切換讀取順序。 例如，您可以按 **Ctrl+右 Shift** 切換 [屬性] 視窗，以支援由右至左讀取屬性值的順序。  
  
不過，並非 Visual Studio 中的所有位置皆支援由右至左的讀取順序。 例外狀況包括：  
  
-   核取方塊、下拉式清單和 Visual Studio 對話方塊中的其他控制項，一律使用由左到右的讀取順序。  
  
-   程式碼編輯器 (和文字編輯器) 不支援由右至左的讀取順序。 您可以使用雙向語言來輸入文字，但讀取順序一律為由左到右。  
  
## <a name="naming-things-using-arabic-or-hebrew-text"></a>使用阿拉伯文或希伯來文文字命名  
 您可以使用阿拉伯文或希伯來文文字，將名稱指派給資料夾、變數或其他物件。 當使用阿拉伯文時，您可以使用任何阿拉伯文字元，包括 Kashida 和讀音符號。  
  
 下列項目可以使用阿拉伯文或希伯來文命名，並在 Visual Studio 中正確處理：  
  
-   方案、專案和檔案名稱，包括您在專案路徑中包含的任何資料夾。 [方案總管] 會正確顯示方案和項目名稱。  
  
-   檔案內容。 您可以使用 Unicode 編碼方式，或使用選取的字碼頁，來開啟或儲存檔案。  
  
    > [!NOTE]
    >  程式碼編輯器是特殊案例。 如需詳細資訊，請參閱下方。  
  
-   資料項目。 伺服器總管會正確顯示下列項目，以供您編輯。  
  
-   複製到 Windows 剪貼簿的項目。  
  
-   屬性和中繼資料。  
  
-   屬性值。 您可以在 [屬性] 視窗中，使用阿拉伯文或希伯來文文字。 此視窗可讓您使用標準的 Windows 按鍵輸入 (**Ctrl+右 Shift** 為由右至左；**Ctrl+左 Shift** 為由左至右)，在由右至左和由左到右的讀取順序之間切換。  
  
-   程式碼和常值文字。 在程式碼編輯器 (亦即文字編輯器) 中，您可以使用阿拉伯文或希伯來文命名類別、函式、變數、屬性、字串常值、屬性等等。 不過，編輯器不支援由右至左的讀取順序；文字一律從左邊界開始。  
  
    > [!TIP]
    > 建議您將字串常值放在資源檔中，而不要在您的程式中直接撰寫 (硬式編碼)。 如需詳細資訊，請參閱[桌面應用程式中的資源 (.NET Framework)](/dotnet/framework/resources/index)。
  
    > [!NOTE]
    > 您必須使用一致的方式來參考以這些語言物名的物件。 例如，若您使用 Kashida 來命名阿拉伯文的變數，則在參考該變數時，您必須一律使用 Kashida，否則會產生錯誤。  
  
-   程式碼註解。 您可以使用阿拉伯文或希伯來文建立註解。 您也可以在註解產生器工具中使用這些語言。  
  
## <a name="see-also"></a>另請參閱

[Windows Forms 應用程式的雙向支援](/dotnet/framework/winforms/advanced/bi-directional-support-for-windows-forms-applications)  
[ASP.NET Web 應用程式的雙向支援](http://msdn.microsoft.com/Library/5576f9b1-9b86-41ef-8354-092d366bcd03)  
[全球化應用程式](../ide/globalizing-applications.md)  
[當地語系化應用程式](../ide/localizing-applications.md)