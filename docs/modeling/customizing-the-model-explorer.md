---
title: 自訂模型總管
description: 瞭解如何為您的網域指定語言設計工具變更 explorer 的外觀和行為。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.dsltools.dsldesigner.explorerbehavior
helpviewer_keywords:
- Domain-Specific Language Tools, Domain-Specific Language Explorer
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b3ae5ea3c24ea72c911f686c7a0a92191785d9d5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99935374"
---
# <a name="customizing-the-model-explorer"></a>自訂模型總管
您可以針對網域專屬的語言設計工具變更 explorer 的外觀和行為，如下所示：

- 變更視窗標題。

- 變更 tab 圖示。

- 變更節點的圖示。

- 隱藏節點。

## <a name="changing-the-window-title"></a>變更視窗標題
 若要變更所產生之瀏覽器的視窗標題，請選取 [ **DSL explorer**] 中的 [ **explorer 行為**]，然後在 [**屬性**] 視窗中，將 [**標題**] 屬性設定為您想要的標題。

## <a name="changing-the-tab-icon"></a>變更 Tab 圖示
 若要變更瀏覽器的索引標籤圖示，請在 .bmp 檔中使用16x16 圖元的圖示。 將圖示檔放在 [\DslPackage\Resources\] 資料夾中，然後將檔案名變更為 **ModelExplorerToolWindowBitmaps.bmp**。 例如，您可以將 Visual Studio 安裝 .ico 圖示檔變更為 .bmp 格式，然後將它重新命名為 **DSLLanguageName\DslPackage\Resources\ModelExplorerToolWindowBitmaps.bmp**。 當您在瀏覽器的索引標籤上停駐在 **方案總管** 一起時，產生的設計工具會在您的瀏覽器上顯示此圖示。

## <a name="setting-custom-icons-on-explorer-nodes"></a>在 Explorer 節點上設定自訂圖示
 您可以使用 explorer 節點設定自訂您 explorer 中的節點。 下列程式說明如何將圖示新增至節點。

#### <a name="to-add-an-icon-to-an-explorer-node"></a>將圖示加入至 explorer 節點

1. [!INCLUDE[dsl](../modeling/includes/dsl_md.md)]使用 [工作流程] 方案範本建立解決方案。

2. 將包含16x16 圖元圖示的 .bmp 檔案放在解決方案的 [ **Dsl\Resources** ] 資料夾中。

3. 在 [ **DSL Explorer**] 中，以滑鼠右鍵按一下 [ **Explorer 行為** ]，然後按一下 [ **加入新的 explorer 節點設定**]。

    **ExplorerNodeSettings** 節點會出現在 [**自訂節點設定**] 節點底下。

4. 選取 [ **ExplorerNodeSettings**]，然後在 [ **屬性** ] 視窗中，將 [ **類別** ] 設定為 [ **執行者**]。

5. 設定 **圖示以顯示** 到圖示檔的路徑。

6. 轉換所有範本，然後建立並執行方案。

7. 在產生的設計工具中，開啟範例圖表。

    Explorer 應該會顯示具有您圖示 **的三個** 動作專案節點。

> [!NOTE]
> 如果您已為產生的瀏覽器中顯示的任何專案設定節點圖示，則所有 explorer 節點都會顯示圖示。 如果未設定任何圖示，節點會顯示預設圖示。

## <a name="changing-the-name-displayed-on-an-explorer-node"></a>變更在 Explorer 節點上顯示的名稱
 您可以變更模型專案的名稱在您的瀏覽器中顯示的方式。 下列程式顯示如何顯示批註節點中 **批註****所參考的工作** 名稱。

#### <a name="to-display-a-property"></a>顯示內容

1. 開啟您在先前程式中建立的方案。

2. 藉由將具有屬性名稱主旨的角色多重性設定為 0 **..1，以** 確定 **批註** 只參考單一網域類別。 屬性名稱應該會成為 **主旨，而** 關聯性名稱應該會變成 **CommentReferencesSubject**。

3. 在 [ **DSL Explorer**] 中，以滑鼠右鍵按一下 [ **Explorer 行為** ]，然後按一下 [ **加入新的 explorer 節點設定**]。

     **ExplorerNodeSettings** 節點會出現在 [**自訂節點設定**] 節點底下。

4. 選取 [ **ExplorerNodeSettings**]，然後在 [ **屬性** ] 視窗中，將 [ **類別** ] 設定為 [ **批註**]。

5. 以滑鼠右鍵按一下 [ **批註** ] 節點，然後按一下 [ **加入新的屬性路徑**]。

     新節點隨即出現，並顯示 [名稱] **屬性**。

6. 選取 [ **顯示內容**]，然後在 [ **屬性** ] 視窗中，按一下 [ **屬性**] 的 [值] 欄位。 選取 [ **批註**]，然後依序選取 [ **CommentReferencesSubject**] 和 [ **FlowElement**]。 產生的路徑應該類似 **CommentReferencesSubject。主旨/！主體**。

7. 在 [ **屬性**] 的 [值] 欄位中，選取 [ **名稱**]。

8. 轉換所有範本，然後建立並執行您的方案。

9. 在產生的設計工具中，開啟範例圖表。

10. 在批註元素與圖表上的 **Task1** 專案之間繪製 **批註接點**。

     Explorer 節點應將批註顯示為 **Task1**。

## <a name="hiding-nodes"></a>隱藏節點
 您可以藉由將節點的路徑新增至 [ **DSL explorer**] 的 [**隱藏節點**] 節點，在您的 [explorer] 中隱藏該節點。 下列程式顯示如何隱藏 **批註** 節點。

#### <a name="to-hide-an-explorer-node"></a>隱藏 explorer 節點

1. 開啟您在先前程式中建立的方案。

2. 在 [ **DSL Explorer**] 中，以滑鼠右鍵按一下 [ **Explorer 行為** ]，然後按一下 [ **加入新的網域路徑**]。

     [ **網域路徑** ] 節點會出現在 [ **隱藏節點**] 下。

3. 選取 [ **網域路徑**]，然後在 [ **屬性** ] 視窗中，按一下 [ **路徑定義**] 的 [值] 欄位。 依序選取 [ **FlowGraph**] 和 [ **FlowGraphHasComments**]。 產生的路徑應該類似 **FlowGraphHasComments 批註。**

4. 轉換所有範本，然後建立並執行您的方案。

5. 在產生的設計工具中，開啟範例圖表。

     Explorer 應該只顯示 [動作專案] 節點，而且不應該顯示 [**批註** **] 節點。**

## <a name="see-also"></a>另請參閱

- [Domain-Specific Language Tools Glossary](/previous-versions/bb126564(v=vs.100)) (特定領域語言工具字彙表)