---
title: 建立 Visual Studio 中設定的自訂程式碼分析規則 |Microsoft 文件
ms.date: 04/04/2018
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.addremoverulesets
helpviewer_keywords:
- Development Edition, rule sets
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 57800f36c3a81e021c1fb40bab1c07bbed3e7f9d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="custom-rule-sets"></a>自訂規則集

您可以建立自訂*規則集*以符合特定專案需求的程式碼分析。

## <a name="create-a-custom-rule-set"></a>建立自訂規則集

若要建立自訂規則集，您可以開啟內建規則集**規則集編輯器**。 從該處，您可以新增或移除的特定規則，而且您可以變更違反規則時所發生的動作&mdash;比方說，顯示警告或錯誤。

1. 在**方案總管] 中**，以滑鼠右鍵按一下專案，然後選取**屬性**。

2. 在**屬性**頁面，選取**程式碼分析**] 索引標籤。

3. 在**執行此規則集**下拉式清單中，執行下列其中一項：

    - 選取您想要自訂的規則集。

     \-或-

    - 選取**\<瀏覽 >** ，指定現有的規則集不在清單中。

4. 選取**開啟**至規則集編輯器中顯示的規則。

您也可以建立新的規則集檔案從**新檔案**對話方塊：

1. 選取**檔案** > **新增** > **檔案**，或按**Ctrl**+**N**.

2. 在**新檔案**對話方塊中，選取**一般**在左側的類別目錄，然後選取 [**程式碼分析規則集**。

3. 選取 [開啟] 。

   新*.ruleset*規則集編輯器中開啟檔案。

### <a name="create-a-custom-rule-set-from-multiple-rule-sets"></a>建立自訂規則集從多個規則集

1. 在方案總管] 中，以滑鼠右鍵按一下專案，然後選取**屬性**。

2. 在**屬性**頁面，選取**程式碼分析**] 索引標籤。

3. 選取**\<選擇多個規則的設定...>**從**執行此規則集**。

4. 在**新增或移除規則集**對話方塊中，選取規則設定您想要包含在新的規則集。

   ![新增或移除規則集對話方塊](media/add-remove-rule-sets.png)

5. 選取**存**，輸入的名稱*.ruleset*檔案，然後再選取**儲存**。

   中已選取新的規則集**執行此規則集**清單。

6. 選取**開啟**開啟新的規則在規則集編輯器中設定。

## <a name="name-and-description"></a>名稱和描述

若要變更編輯器中開啟的規則集的顯示名稱，請開啟**屬性**視窗選取**檢視** > **屬性] 視窗**功能表列上。 輸入中的顯示名稱**名稱**方塊。 您也可以輸入規則集的描述。

## <a name="next-steps"></a>後續步驟

既然您已設定的規則下, 一個步驟是自訂的規則，藉由新增或移除規則，或修改規則違規的嚴重性。

> [!div class="nextstepaction"]
> [修改規則集編輯器中的規則](../code-quality/working-in-the-code-analysis-rule-set-editor.md)

## <a name="see-also"></a>另請參閱

- [如何：設定 Managed 程式碼專案的程式碼分析](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)
- [程式碼分析規則集參考](../code-quality/rule-set-reference.md)