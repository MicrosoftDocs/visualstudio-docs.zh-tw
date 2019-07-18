---
title: Microsoft 語言介面套件 (LIP) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
helpviewer_keywords:
- text [Visual Studio], multiple languages
- Multilingual User Interface [Visual Studio]
- language switching [Visual Studio]
- MUI [Visual Studio]
- multiple language support [Visual Studio SDK]
- Windows Multilingual User Interface
- UI text language [Visual Studio]
- languages, multiple language support
ms.assetid: dc86304b-65b7-47e6-9314-1dfd02ecfa65
caps.latest.revision: 28
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 503f97d1530f8d22184f42a2452046782a997c18
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63433003"
---
# <a name="microsoft-language-interface-packs-lips-and-visual-studio"></a>Microsoft 語言介面套件 (LIP) 和 Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以使用 Windows 語言介面套件 (LIP) 安裝某個語言版本的 Windows，然後再安裝各種使用者介面語言套件。 使用者介面語言套件會提供作業系統的當地語系化使用者介面 (UI)。 例如，您可在 Windows 英文版之上安裝日文語言介面套件，之後便能在日文和英文的 Windows UI 語言間切換。 透過 LIP，您可以在一部電腦上擁有多種語言版本的 Windows。

 在安裝 LIP 和多種語言版本 Visual Studio 的電腦上，變更 Windows 顯示語言設定會在安裝相符語言套件時，同時設定 Windows 和 Visual Studio。

## <a name="limitations-of-multi-language-installations"></a>多語言安裝的限制
 在同一部電腦上安裝不同語言版本的 Visual Studio 時，您只能在相符版本之間切換語言。 例如，如果您安裝一個英文 Express 版、一個德文 Express 版和一個 Professional 版，則只能切換 Express 版的語言，而無法切換 Professional 版的語言。

 Visual Studio 使用統一的語言套件。 若要為這些產品安裝多個語言版本，您必須先安裝某個語言的完整產品，再安裝一個或多個語言套件。

> [!NOTE]
> Visual Studio 不支援在同一部電腦上多次安裝不同語言版本的完整產品。 安裝某個語言的完整產品之後，您必須使用語言套件來加入其他語言版本。 在 Express 版中，您仍可以在同一部電腦上多次安裝不同語言版本的完整產品。

### <a name="support-for-code-pages"></a>字碼頁支援
 如果文字中包含不屬於目前字碼頁的字元，某些 Visual Studio 工具將無法正確顯示文字。 這些工具會改為顯示問號，或表示文字已損毀。 受影響的工具或區域如下：

- 使用 FTP 部署的網站。

- 某些控制項上的非 ASCII 電腦名稱。

- 在 Visual Studio 外部執行的命令列工具。

- Visual Basic 移轉精靈。

- ActiveX 控制項測試容器。

- OLE/COM 物件檢視器。

- ISAPI Web 偵錯工具。

- 具有 HTML 說明內容的 MFC 應用程式專案。

- 有不相容的字碼頁時，Visual SourceSafe / SCCI UI 會回復為英文。

- Visual SourceSafe 不支援 Unicode 檔名。

- 無法將終端使用者定義的字元 (私用區域) 當做語彙基元/識別項使用。

- 將 Windows 字碼頁設定為東亞語言時，無法在某些 Visual Studio 工具視窗中顯示拉丁文擴充- B 字元。

- 由多種語言字集中的字元所組成的文字執行，可能會為某些字元顯示預設字符。

- 複製複雜字集字串並貼到通用控制項時，可能會造成字元外形遺失。 請改用對應的語言鍵盤來輸入文字。

##### <a name="to-correctly-display-characters-that-are-not-included-in-the-current-code-page"></a>正確顯示目前字碼頁中不包含的字元

1. 依序按一下 [開始] 和 [控制台]，然後開啟 [地區及語言選項] (在 [!INCLUDE[win8](../includes/win8-md.md)] 中為 [區域])。

    > [!NOTE]
    > 您必須是電腦的系統管理員，才能依照這些步驟進行。

2. 按一下 [進階] 按鈕。

3. 在 [選取一個符合您要使用之非 Unicode 程式語言版本的語言] 清單中，選取您目前使用的語言。

4. 按一下 [確定]。

## <a name="changing-the-language-used-for-the-ui-text-in-visual-studio"></a>變更 Visual Studio 中 UI 文字所使用的語言
 當您在同一部電腦上安裝 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 的多個語言版本時，[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] UI 會預設為 [與 Microsoft Windows 相同]。 這項設定表示 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 會以指定為作業系統顯示語言的語言來顯示 UI 文字。

> [!NOTE]
> 如果將 Visual Studio 設定為使用 [與 Microsoft Windows 相同]，且未安裝相符的 Visual Studio 語言套件，則 Visual Studio 會使用 Visual Studio 第一次安裝的語言。

#### <a name="to-set-the-language-that-is-used-for-the-ui-text-in-visual-studio"></a>設定 Visual Studio 中 UI 文字所使用的語言

1. 在 [ **工具** ] 功能表上按一下 [ **選項**]。

2. 在 [選項] 對話方塊中，展開 [環境]，然後按一下 [國際設定]。

3. 在 [語言] 清單中，選擇 UI 文字應在開發環境中用來顯示的語言。

    若要讓 IDE 中的 UI 文字符合作業系統顯示語言設定，請選取 [與 Microsoft Windows 相同]。

   您也可以使用 devenv 命令來設定 UI 所使用的語言。 如需詳細資訊，請參閱 [/LCID (devenv.exe)](../ide/reference/lcid-devenv-exe.md)。

## <a name="see-also"></a>請參閱
 [選項對話方塊、環境、國際設定](../ide/reference/international-settings-environment-options-dialog-box.md)