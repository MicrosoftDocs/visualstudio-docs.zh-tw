---
title: 阿拉伯文和希伯來文應用程式的支援
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Hebrew character display, creating applications
- bidirectional language support, about bidirectional language support
- Arabic language, creating applications
ms.assetid: b56f9795-ed8d-4452-9d49-8ca0b0145d86
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 21851bc26ec69207c95a41e988b20b5df3c70c39
ms.sourcegitcommit: b7f25ae08e45fcaa84a84276b588cf6799cc7620
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/07/2019
ms.locfileid: "57567256"
---
# <a name="create-applications-in-bidirectional-languages"></a>建立使用雙向語言的應用程式

您可以使用 Visual Studio 來建立應用程式，以正確顯示由右至左撰寫的語言文字，包括阿拉伯文和希伯來文。 針對某些功能，您可以直接設定屬性， 若為其他情況，則必須在程式碼中實作功能。

> [!NOTE]
> 若要輸入及顯示雙向語言，您必須使用已設定適當語言的 Windows 版本。 這包括已安裝適當語言套件的英文版 Windows，或正確的 Windows 當地語系化版本。

## <a name="types-of-applications-that-support-bidirectional-languages"></a>支援雙向語言的應用程式類型

-  Windows 應用程式

   您可以建立完整的雙向應用程式，以支援雙向文字、由右至左讀取順序及鏡像功能 (將視窗、功能表、對話方塊等配置反轉)。 除了鏡像功能以外，這些功能皆為預設提供或以屬性設定形式提供。 某些功能 (例如訊息方塊) 本身就支援鏡像， 但若為其他情況，則必須在程式碼中實作鏡像。 如需詳細資訊，請參閱 [Windows Forms 應用程式的雙向支援](/dotnet/framework/winforms/advanced/bi-directional-support-for-windows-forms-applications)。

-  Web 應用程式

   Web 服務支援 UTF-8 和 Unicode 文字的接收與傳送作業，因此非常適合使用雙向語言的應用程式。 Web 用戶端應用程式需仰賴瀏覽器來呈現其使用者介面；因此，Web 應用程式的雙向支援程度與使用者瀏覽器對這些雙向功能的支援程度相關。 在 Visual Studio 中，您可以建立支援阿拉伯文或希伯來文文字、由右至左的讀取順序、檔案編碼方式及當地文化特性設定的應用程式。 如需詳細資訊，請參閱 [ASP.NET Web 應用程式的雙向支援](https://msdn.microsoft.com/Library/5576f9b1-9b86-41ef-8354-092d366bcd03)。

主控台應用程式不支援雙向語言的文字。 這是搭配使用 Windows 與主控台應用程式產生的後果。

## <a name="fully-supported-features"></a>完整支援的功能

在 Visual Studio 的設計階段中，您可以透過下列方式來使用雙向語言：

- **文字輸入**

   Visual Studio 支援 Unicode，因此如果您的系統已設好適當的地區設定和輸入語言，即可使用阿拉伯文或希伯來文輸入文字。 (阿拉伯文支援包括 Kashida 和讀音符號)。

- **物件名稱**

   您可以使用雙向語言將名稱指派給解決方案、專案、檔案、資料夾等。 在程式碼中，您可以針對變數、類別、物件、屬性、中繼資料以及其他項目的名稱使用雙向語言。

- **檔案編碼**

   您可以使用特定語言或 Unicode 編碼儲存及開啟檔案。 如需詳細資訊，請參閱[如何：以編碼來儲存及開啟檔案](../ide/how-to-save-and-open-files-with-encoding.md)。

## <a name="features-with-limited-support"></a>有限支援的功能

### <a name="right-to-left-reading-order"></a>由右至左的讀取順序

根據預設，Visual Studio 中的文字輸入控制項採用由左至右的讀取順序。 在大部分情況下，您可以使用標準 Windows 筆勢來切換讀取順序。 例如，您可以按 **Ctrl**+**RightShift** 切換 [屬性] 視窗，以支援由右至左讀取屬性值的順序。 不過，並非 Visual Studio 中的所有位置皆支援由右至左的讀取順序：

- 核取方塊、下拉式清單和 Visual Studio 對話方塊中的其他控制項，一律使用由左到右的讀取順序。

- 程式碼編輯器 (和文字編輯器) 不支援由右至左的讀取順序。 您可以使用雙向語言來輸入文字，但讀取順序一律為由左到右。

## <a name="arabic-or-hebrew-object-names"></a>阿拉伯文或希伯來文物件名稱

您可以使用阿拉伯文或希伯來文文字，將名稱指派給資料夾、變數或其他物件。 當使用阿拉伯文時，您可以使用任何阿拉伯文字元，包括 Kashida 和讀音符號。

下列元素可以使用阿拉伯文或希伯來文命名，並在 Visual Studio 中正確處理：

- 方案、專案和檔案名稱，包括您在專案路徑中包含的任何資料夾。 [方案總管] 會正確顯示解決方案和元素名稱。

- 檔案內容。 您可以使用 Unicode 編碼方式，或使用選取的字碼頁，來開啟或儲存檔案。

    > [!NOTE]
    > 程式碼編輯器不支援由右至左的讀取順序。

- 資料項目。 [伺服器總管] 會正確顯示這些元素，並可讓您編輯。

- 複製到 Windows 剪貼簿的項目。

- 屬性和中繼資料。

- 屬性值。 您可以在 [屬性] 視窗中，使用阿拉伯文或希伯來文文字。 此視窗可讓您使用標準 Windows 按鍵輸入 (**Ctrl**+**RightShift** 為由右至左；**Ctrl**+**LeftShift** 為由左至右)，在由右至左和由左至右的讀取順序之間切換。

- 程式碼和常值文字。 在程式碼編輯器中，您可以使用阿拉伯文或希伯來文命名類別、函式、變數、屬性、字串常值、屬性等。 不過，編輯器不支援由右至左的讀取順序；文字一律從左邊界開始。

    > [!TIP]
    > 您應將字串常值放在資源檔中，而不是直接寫在您的程式中。 如需詳細資訊，請參閱[桌面應用程式中的資源 (.NET Framework)](/dotnet/framework/resources/index)。

    > [!NOTE]
    > 您必須使用一致的方式來參考以阿拉伯文和希伯來文命名的物件。 例如，若您使用 Kashida 來命名阿拉伯文變數，則在參考該變數時，您必須一律使用 Kashida，否則會產生錯誤。

- 程式碼註解。 您可以使用阿拉伯文或希伯來文建立註解。 您也可以在註解產生器工具中使用這些語言。