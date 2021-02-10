---
title: 阿拉伯文和希伯來文的支援
description: 瞭解如何顯示阿拉伯文和希伯來文文字，以及輸入物件名稱和值的雙向文字。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Hebrew character display [Visual Studio]
- bidirectional language support
- Arabic, creating applications
ms.assetid: b56f9795-ed8d-4452-9d49-8ca0b0145d86
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a16aa4d445878ac8d357fa551e46552a1465bfe1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99971345"
---
# <a name="support-for-bidirectional-languages-in-visual-studio"></a>Visual Studio 中的雙向語言支援

Visual Studio 可以正確顯示阿拉伯文和希伯來文文字，並讓您針對物件名稱和值輸入雙向文字。

> [!NOTE]
> 若要輸入及顯示雙向語言，您必須使用已設定適當語言的 Windows 版本。 這包括已安裝適當語言套件的英文版 Windows，或正確的 Windows 當地語系化版本。

## <a name="fully-supported-features"></a>完整支援的功能

在 Visual Studio 的設計階段期間，您可以在輸入文字、為物件命名，以及儲存及開啟檔案時使用雙向語言。

### <a name="text-entry"></a>文字輸入

Visual Studio 支援 Unicode，因此如果您的系統已設好適當的地區設定和輸入語言，即可使用阿拉伯文或希伯來文輸入文字。 (阿拉伯文支援包括 Kashida 和讀音符號)。

### <a name="arabic-or-hebrew-object-names"></a>阿拉伯文或希伯來文物件名稱

您可以使用雙向語言將名稱指派給解決方案、專案、檔案、資料夾等。 在程式碼中，您可以針對變數、類別、物件、屬性、中繼資料以及其他項目的名稱使用雙向語言。 當使用阿拉伯文時，您可以使用任何阿拉伯文字元，包括 Kashida 和讀音符號。

下列元素可以使用阿拉伯文或希伯來文命名，並能由 Visual Studio 正確處理：

- 方案、專案和檔案名稱，包括您在專案路徑中包含的任何資料夾。

   [方案總管] 會正確顯示解決方案和元素名稱。

- 檔案內容。

   您可以使用 Unicode 編碼方式，或使用選取的字碼頁，來開啟或儲存檔案。

- 資料項目。

   [伺服器總管] 會正確顯示這些元素，並可讓您編輯它們。

- 複製到 Windows 剪貼簿的項目。

- 屬性和中繼資料。

- 屬性值。

   您可以在 [ **屬性** ] 視窗中使用阿拉伯文或希伯來文文字。 視窗可讓您使用標準 Windows 擊鍵 (**ctrl** + **右 shift** （由右至左）和 **ctrl** + **LeftShift** （由) 左至右）從右至左和由左到右的讀取順序進行切換。

- 程式碼和常值文字。

   在程式碼編輯器中，您可以使用阿拉伯文或希伯來文命名類別、函式、變數、屬性、字串常值、屬性等。 不過，編輯器不支援由右至左的讀取順序；文字一律從左邊界開始。

   > [!TIP]
   > 您應將字串常值放在資源檔中，而不是直接寫在您的程式中。 如需詳細資訊，請參閱[桌面應用程式中的資源 (.NET Framework)](/dotnet/framework/resources/index)。

   > [!NOTE]
   > 您必須使用一致的方式來參考以阿拉伯文和希伯來文命名的物件。 例如，若您使用 Kashida 來命名阿拉伯文變數，則在參考該變數時，您必須一律使用 Kashida，否則會產生錯誤。

- 程式碼註解。 您可以使用阿拉伯文或希伯來文建立註解。 您也可以在註解產生器工具中使用這些語言。

### <a name="file-encoding"></a>檔案編碼

您可以使用特定語言或 Unicode 編碼儲存及開啟檔案。 如需詳細資訊，請參閱 [如何：使用編碼方式儲存及開啟](../ide/how-to-save-and-open-files-with-encoding.md)檔案。

## <a name="right-to-left-reading-order"></a>由右至左的讀取順序

Visual Studio 只能有限地支援從右至左的讀取順序。 根據預設，Visual Studio 中的文字輸入控制項採用由左至右的讀取順序。 在大部分情況下，您可以使用標準 Windows 筆勢來切換讀取順序。 例如，您可以按 **Ctrl** + **右 shift** 切換 [**屬性**] 視窗，以支援由右至左讀取屬性值的順序。

Visual Studio 中的下列位置並不支援從右至左的讀取順序：

- 核取方塊、下拉式清單和 Visual Studio 對話方塊中的其他控制項，一律使用由左到右的讀取順序。

- 程式碼編輯器 (和文字編輯器) 不支援由右至左的讀取順序。 您可以使用雙向語言來輸入文字，但讀取順序一律為由左到右。

## <a name="see-also"></a>另請參閱

- [開發全球化和當地語系化應用程式](globalizing-and-localizing-applications.md)
