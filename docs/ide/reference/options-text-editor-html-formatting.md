---
title: 選項、文字編輯器、HTML (Web Form)、格式
description: 瞭解如何使用 [HTML] 區段中的 [格式化] 頁面，在程式碼編輯器中設定程式碼格式化的 HTML 專案選項。
ms.custom: SEO-VS-2020
ms.date: 1/15/2019
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.HTML.Format
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e3c8fe85b7bce856867802d43411816ae2df5d2c
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040975"
---
# <a name="options-text-editor-html-web-forms-formatting"></a>選項、文字編輯器、HTML (Web Form)、格式

使用 [格式] 選項頁面，可設定在程式碼編輯器中用於程式碼格式設定的 HTML 專案選項。 若要存取此頁面，請在功能表列上選擇 [**工具**  >  **選項**]，然後展開 [**文字編輯器**  >  **HTML (Web Form)**  >  **格式**]。

## <a name="capitalization"></a>大寫

選取這些選項時，[原始碼] 檢視和 XML 編輯器會在首次建立元素時和自動格式化期間，將大小寫格式套用至元素和屬性的名稱。 [套用自動格式化] 設定會決定自動重新格式化的時機。

> [!WARNING]
> XML 會區分大小寫。 設定預設大小寫會影響 XML 剖析器。

### <a name="uielement-list"></a>UIElement 清單

**伺服器標記、伺服器屬性**

這些選項會指定 Web 伺服器控制項之標記的大寫方式。

|選項|結果|
|---------------------------------|------------------------------|
|**同輸入**|元素的大小寫和您輸入的完全相同。|
|**大寫**|元素名稱重新格式化為大寫。|
|**小寫**|元素名稱重新格式化為小寫。|
|**組件定義**|元素大小寫由元素在對應型別類別中的定義方式決定。|

**用戶端標記、用戶端屬性**

這些選項會指定自動格式化是否要將 HTML 屬性 (Attribute) 和屬性 (Property) 的名稱改為大寫或小寫，或是保持輸入的原樣。

|選項|結果|
|---------------------------------|------------------------------|
|**同輸入**|屬性的大小寫和您輸入的完全相同。|
|**大寫**|屬性名稱重新格式化為大寫。|
|**小寫**|屬性名稱重新格式化為小寫。|

## <a name="automatic-formatting-options"></a>自動格式化選項

這些選項會導致 [原始碼檢視] 編輯器在自動格式化期間，新增或移除實體分行符號。 您也可以指定編輯器是否要在屬性前後加上引號。

> [!NOTE]
> 這些設定不會改變 XML 標記的空白區。

### <a name="uielement-list"></a>UIElement 清單

- **輸入時插入屬性值引號**

   選取此選項時，編輯器會在您輸入 (時，自動在屬性前後加上引號，例如： ID = "Select1" ) 。 如果想要手動插入標記的引號，請清除這個選項。

   > [!NOTE]
   > 無論是否選取這個選項，都會保留標記中的所有現有引號，永遠不會移除引號。

- **格式化時插入屬性值引號**

   選取此選項時，自動格式化會在屬性值前後加上引號 (例如： ID = "Select1" ) 。

   > [!NOTE]
   > 無論是否選取這個選項，都會保留標記中的所有現有引號。

- **自動插入結尾標記**

   選取此選項時，編輯器會自動建立結束記號 (例如， **\</b>** 當您關閉開頭標記時) 。

## <a name="tag-wrapping"></a>標記換行

這些選項決定編輯器是否將超出一定長度的標籤分行。

### <a name="uielement-list"></a>UIElement 清單

- **標記超出指定長度時換行**

   選取時，如果標籤超過您在 [長度] 文字方塊中指定的長度，編輯器會將標籤分在不同行。 此動作只在設定標籤格式時發生，而不在輸入新標籤時發生。

   > [!NOTE]
   > 您指定的值是做為最小值使用。 編輯器不會分開個別屬性。

- **長度**

   指定一行顯示的字元數，超過此長度後即換行顯示。 選取 [標記超出指定長度時換行] 方塊後才能使用此輸入方塊。

- **標籤專用選項**

   顯示 [標籤專用選項] 對話方塊，可讓您設定個別標籤或標籤群組的格式。

## <a name="see-also"></a>另請參閱

- [選項對話方塊、環境、一般](../../ide/reference/general-environment-options-dialog-box.md)
