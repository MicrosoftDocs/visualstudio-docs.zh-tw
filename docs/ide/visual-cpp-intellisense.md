---
title: C++ IntelliSense
description: 瞭解您可以在撰寫 c + + 專案的程式碼時使用的一些 IntelliSense 功能。
ms.custom: SEO-VS-2020
ms.date: 10/08/2018
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 49d555b2e509237e34375e1b85a35c57a6db4f3b
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2020
ms.locfileid: "96478883"
---
# <a name="visual-c-intellisense-features"></a>Visual C++ IntelliSense 功能

IntelliSense 是一組功能的名稱，這些功能可讓撰寫程式碼變得更方便。 IntelliSense for C++ 適用於獨立檔案以及屬於 C++ 專案的檔案。 在跨平臺專案中，某些 IntelliSense 功能可用於共用程式碼專案中的 *.cpp* 和 *.c* 檔，即使您是在 Android 或 iOS 內容中也一樣。

此文章提供 C+ + IntelliSense 功能的概觀。 如需為專案設定 IntelliSense 與如何針對問題進行疑難排解的詳細資訊，請參閱[設定 C++ IntelliSense 專案](visual-cpp-intellisense-configuration.md)。

## <a name="intellisense-features-in-c"></a>C++ 中的 IntelliSense 功能

IntelliSense 是一組功能的名稱，這些功能可讓撰寫程式碼變得更方便。 由於不同的人對於方便有不同的想法，因此幾乎所有的 IntelliSense 功能都能在 [文字編輯器] > [C/C++] > [進階] 屬性頁下的 [選項] 對話方塊中啟用或停用。 請從功能表列上的 [工具] 功能表使用 [選項] 對話方塊。

![[工具選項] 對話方塊](../ide/media/sintellisensecpptoolsoptions.PNG)

您可以使用如下圖所示的功能表項目和鍵盤快速鍵來存取 IntelliSense。

![IntelliSense 功能表](../ide/media/vs2015_cpp_intellisense_menu.png)

## <a name="statement-completion-and-member-list"></a>陳述式完成和成員清單

當您開始輸入關鍵字、型別、函式、變數名稱或其他編譯器可辨識的程式元素時，編輯器會提供建議，幫您自動完成文字。

如需圖示及其意義的清單，請參閱 [類別檢視和物件瀏覽器圖示](../ide/class-view-and-object-browser-icons.md)。

![Visual C&#43;&#43; 自動完成文字視窗](../ide/media/vs2015_cpp_complete_word.png)

您第一次叫用成員清單時，它只會顯示目前內容可存取的成員。 如果您在這之後按下 **Ctrl** + **J** ，則會顯示所有成員，而不考慮存取範圍。 如果您第三次叫用它，會顯示更多的程式項目清單。 您可以在 [文字編輯器] > [C/C++] > [一般] > [自動列出成員] 下的 [選項] 對話方塊中關閉成員清單。

![Visual C&#43;&#43; 成員清單](../ide/media/vs2015_cpp_list_members.png)

## <a name="parameter-help"></a>參數說明

當您輸入函式呼叫的左括號或在類別樣板變數宣告上的角括號時，編輯器會顯示一個小視窗，其中具有每個函式或建構函式多載的參數類型。 「目前」參數會根據游標位置以粗體顯示。 您可以在 [文字編輯器] > [C/C++] > [一般] > [參數資訊] 下的 [選項] 對話方塊中關閉參數資訊。

![Visual C&#43;&#43; 參數說明](../ide/media/vs_2015_cpp_param_help.png)

## <a name="quick-info"></a>快速諮詢

當您將滑鼠游標停留在變數時，會內嵌出現一個小視窗，其中顯示類型資訊和類型定義所在的標頭。 將游標暫留在函式呼叫，可查看函式的簽章。 您可以在 [文字編輯器] > [C/C++] > [一般] > [自動快速諮詢] 下的 [選項] 對話方塊中關閉快速諮詢。

![Visual C&#43;&#43; QuickInfo](../ide/media/vs2015_cpp_quickinfo.png)

## <a name="error-squiggles"></a>錯誤波浪線

程式項目 (變數、關鍵字、大括號、類型名稱等等) 下的波浪線會提醒您注意程式碼中的錯誤或潛在錯誤。 當您撰寫向前宣告時，會出現綠色波浪線，提醒您仍然需要撰寫實作。 當目前不在作用中的程式碼中有錯誤時 (例如在 Windows 內容中工作時輸入了在 Android 內容中會是錯誤的內容)，紫色波浪線就會顯示在共用的專案中。 紅色波浪線表示在使用中程式碼中，有需要處理的編譯器錯誤或警告。

![Visual C&#43;&#43; 錯誤波浪線](../ide/media/vs2015_cpp_error_quiggles.png)

### <a name="code-colorization-and-fonts"></a>程式碼顏色標示和字型

預設色彩和字型可以在 [環境] > [字型和色彩] 下的 [選項] 對話方塊中變更。 您可以在這裡變更許多 UI 視窗的字型，而不只是編輯器。 C++ 特有的設定會以 "C++" 為開頭；其他設定則適用於所有語言。

## <a name="cross-platform-intellisense"></a>跨平台 IntelliSense

在共用程式碼專案中，即使您正在 Android 的內容中工作，也可以使用某些 IntelliSense 功能，例如波浪線。 如果您撰寫一些會導致非作用中專案發生錯誤的程式碼，IntelliSense 仍會顯示波浪線，但色彩會與目前內容中的錯誤波浪線不同。

請考慮設定為針對 Android 和 iOS 建置的 OpenGLES 應用程式。 圖例顯示正在編輯共用程式碼。 在此圖中，使用中的專案是 **iOS.StaticLibrary**：

![已將 iOS 選取為作用中的專案。](../ide/media/intellisensecppcrossplatform2.png)

請注意：

- 第 6 行上的 `#ifdef` 分支呈現灰色，表示非使用中的區域，因為 `__ANDROID__` 不是針對 iOS 專案而定義。

- 位於第 11 行的問候語變數會使用識別碼 `HELLO` 進行初始化，現在它具有紅色波浪線。 這是因為目前使用中的 iOS 專案中並未定義任何識別碼 `HELLO`。

- 第 12 行會在識別碼 `BYE` 具有紫色波浪線；此識別項不會在目前選取的非使用中 **Android.NativeActivity** 專案中定義。 即使當 iOS 是使用中專案時這一行會編譯，但 Android 是使用中專案時卻不會編譯。 由於這是共用程式碼，即使它在目前使用中的組態中會編譯，您仍應該更正程式碼。

如果您將使用中專案變更為 Android，波浪線就會變更：

- 第 8 行上的 `#else` 分支呈現灰色，表示非使用中的區域，因為 `__ANDROID__` 是針對 Android 專案而定義。

- 位於第 11 行的問候語變數會使用識別碼 `HELLO` 進行初始化，即具有紫色波浪線。 這是因為目前非使用中的 iOS 專案中並未定義任何識別碼 `HELLO`。

- 第 12 行在識別碼 `BYE` 上具有紅色波浪線，因為此識別碼未在使用中專案內定義。

## <a name="intellisense-for-stand-alone-files"></a>獨立檔案的 IntelliSense

當您開啟任何專案以外的單一檔案時，仍可使用 IntelliSense。 您可以在 [文字編輯器] > [C/C++] > [進階] 下的 [選項] 對話方塊中啟用或停用特定的 IntelliSense 功能。 若要針對不是專案一部分的單一檔案設定 IntelliSense，請尋找 [非專案檔案的 IntelliSense 及瀏覽功能] 區段。

![Visual C&#43;&#43; 單一檔案 IntelliSense](../ide/media/vs2015_cpp_single_file_intellisense.png)

依預設，單一檔案 IntelliSense 僅使用標準 include 目錄來尋找標頭檔。 若要新增其他目錄，請開啟 [方案] 節點上的捷徑功能表，並將您的目錄新增至 [偵錯原始程式檔] 清單，如下圖所示：

![將路徑加入標頭檔。](../ide/media/intellisensedebugyourcode.jpg)

## <a name="enable-or-disable-features"></a>啟用或停用功能

由於不同的人對於方便有不同的想法，因此幾乎所有的 IntelliSense 功能都能在 [文字編輯器] > [C/C++] > [進階] 屬性頁下的 [選項] 對話方塊中啟用或停用。 請從功能表列上的 [工具] 功能表使用 [選項] 對話方塊。

![[工具選項] 對話方塊](../ide/media/sintellisensecpptoolsoptions.PNG)

## <a name="see-also"></a>另請參閱

- [使用 IntelliSense](../ide/using-intellisense.md)
- [設定 C++ IntelliSense 專案](visual-cpp-intellisense-configuration.md)
