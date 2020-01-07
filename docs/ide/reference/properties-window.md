---
title: 屬性視窗
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- properties [Visual Studio], Properties Window
- handler functions, Properties window
- handlers, Properties window
- Windows messages
- properties [Visual Studio], setting at design time
- properties [Visual Studio], editing
- Property Browser
- Windows messages, adding message handlers
- Properties window, overrides
- virtual functions, Properties window
- Properties window
ms.assetid: e6e0fa4f-75c4-4a52-af15-281cd61876ca
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d1be1d4fa9f1b088547bb21dfb64254209783d7e
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2020
ms.locfileid: "75565704"
---
# <a name="properties-window"></a>[屬性] 視窗

使用這個視窗來檢視和變更設計階段屬性，以及位於編輯器和設計工具中的選定物件的事件。 您也可以使用 [屬性] 視窗來編輯和檢視檔案、專案和解決方案屬性。 您可以在 [檢視] 功能表上找到 [屬性] 視窗。 您也可以按 **F4**，或在搜尋方塊中鍵入**屬性**來開啟它。

[屬性] 視窗會顯示不同類型的編輯欄位，根據特定屬性的需求而定。 這些編輯欄位包含自訂編輯器對話方塊用的編輯方塊、下拉式清單和連結。 以灰色顯示的屬性為唯讀。

## <a name="uielement-list"></a>UIElement 清單

物件名稱\
列出目前選取的物件。 只能看見使用中編輯器或設計工具的物件。 當您選取多個物件時，只會顯示所有選取物件共用的屬性。

已分類\
依分類列出所選取物件的所有屬性和屬性值。 您可以摺疊分類來縮減可見屬性的數目。 在展開或摺疊類別目錄時，您可以在類別目錄名稱的左邊看到加號 (+) 或減號 (-)。 分類是依字母順序列出。

字母順序\
依字母順序排序所選物件的所有設計階段屬性和事件。 若要編輯未呈暗灰色的屬性，按一下其右邊的儲存格，並輸入變更。

屬性頁\
顯示所選取項目的 [屬性頁] 對話方塊或 [專案設計工具]。 [屬性頁] 會顯示 [屬性] 視窗中可用屬性的子集、相同屬性或超集。 您可以使用這個按鈕來檢視和編輯與您專案之使用中設定相關的屬性。

屬性\
顯示物件的屬性。 許多物件也有事件，您可以使用 [屬性] 視窗來檢視。

依屬性來源排序\
依來源將屬性分組，例如繼承、套用樣式和繫結。 只有在設計工具中編輯 XAML 檔案時才可使用。

事件\
顯示物件的事件。

> [!NOTE]
> 這個 [屬性] 視窗工具列控制項，只有在表單或控制項設計工具在 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 專案的內容使用中時才可使用。 編輯 XAML 檔案時，事件會出現在 [屬性] 視窗的個別索引標籤。

訊息\
列出所有 Windows 訊息。 可讓您新增或刪除為所選類別提供之訊息的指定處理常式函式。

> [!NOTE]
> 這個 [屬性] 視窗工具列控制項，只有在 [類別檢視] 是 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 專案內容的使用中視窗時才可使用。

覆寫\
列出所選類別的所有虛擬函式，並可讓您新增或刪除覆寫的函式。

> [!NOTE]
> 這個 [屬性] 視窗工具列控制項，只有在 [類別檢視] 是 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 專案內容的使用中視窗時才可使用。

描述窗格\
顯示屬性類型和屬性的簡短描述。 您可以使用快速鍵功能表上的 [描述] 命令，來關閉和開啟屬性的描述。

> [!NOTE]
> 這個 [屬性] 視窗工具列控制項，在設計工具裡編輯 XAML 檔案時無法使用。

縮圖檢視\
在設計工具中編輯 XAML 檔案時，顯示目前選取項目的視覺表示法。

搜尋\
提供在設計工具中編輯 XAML 檔案時，屬性和事件的搜尋功能。 [搜尋] 方塊會回應部分文字搜尋，並在您鍵入時更新搜尋結果。

## <a name="see-also"></a>請參閱

- [專案屬性參考](../../ide/reference/project-properties-reference.md)
- [自訂視窗版面配置](../../ide/customizing-window-layouts-in-visual-studio.md)
