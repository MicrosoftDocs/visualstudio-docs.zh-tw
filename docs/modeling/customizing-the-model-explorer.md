---
title: 自訂模型總管
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.dsltools.dsldesigner.explorerbehavior
helpviewer_keywords:
- Domain-Specific Language Tools, Domain-Specific Language Explorer
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 625ba0d592d0dbdaa8cb910c366852fe32c5f220
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/30/2020
ms.locfileid: "85548365"
---
# <a name="customizing-the-model-explorer"></a>自訂模型總管
您可以針對特定領域語言設計工具變更 explorer 的外觀和行為，如下所示：

- 變更視窗標題。

- 變更索引標籤圖示。

- 變更節點的圖示。

- 隱藏節點。

## <a name="changing-the-window-title"></a>變更視窗標題
 若要變更所產生之 explorer 的視窗標題，請在 [ **DSL explorer**] 中選取 [ **explorer 行為**]，然後在 [**屬性**] 視窗中，將 [**標題**] 屬性設定為您想要的標題。

## <a name="changing-the-tab-icon"></a>變更索引標籤圖示
 若要變更 explorer 的索引標籤圖示，請在 .bmp 檔案中使用16x16 圖元的圖示。 將圖示檔放在 \DslPackage\Resources\ 資料夾中，然後將檔案名變更為**ModelExplorerToolWindowBitmaps.bmp**。 例如，您可以將 Visual Studio 安裝程式 .ico 圖示檔變更為 .bmp 格式，並將它重新命名為**DSLLanguageName\DslPackage\Resources\ModelExplorerToolWindowBitmaps.bmp**。 產生的設計工具會在您的瀏覽器的索引標籤上，當它與**方案總管**停駐在一起時，顯示此圖示。

## <a name="setting-custom-icons-on-explorer-nodes"></a>設定 Explorer 節點上的自訂圖示
 您可以使用 [explorer] 節點設定自訂您的 explorer 中的節點。 下列程式顯示如何將圖示新增至節點。

#### <a name="to-add-an-icon-to-an-explorer-node"></a>將圖示加入至 explorer 節點

1. [!INCLUDE[dsl](../modeling/includes/dsl_md.md)]使用 [工作流程] 方案範本來建立方案。

2. 將包含16x16 圖元圖示的 .bmp 檔案放在解決方案的 [ **Dsl\Resources** ] 資料夾中。

3. 在 [ **DSL Explorer**] 中，以滑鼠右鍵按一下 [ **Explorer 行為**]，然後按一下 [**加入新的 explorer 節點設定**]。

    [ **ExplorerNodeSettings** ] 節點會出現在 [**自訂節點設定**] 節點底下。

4. 選取 [ **ExplorerNodeSettings**]，然後在 [**屬性**] 視窗中，將 [**類別**] 設定為 [**執行者**]。

5. 設定**圖示以顯示**到圖示檔的路徑。

6. 轉換所有範本，然後建立並執行方案。

7. 在產生的設計工具中，開啟範例圖表。

    Explorer 應該會**顯示三個**具有您圖示的動作專案節點。

> [!NOTE]
> 如果您已為所產生之 explorer 中顯示的任何元素設定節點圖示，所有的 explorer 節點都會顯示圖示。 如果未設定任何圖示，節點將會顯示預設圖示。

## <a name="changing-the-name-displayed-on-an-explorer-node"></a>變更 Explorer 節點上顯示的名稱
 您可以變更模型專案的名稱在您的瀏覽器中顯示的方式。 下列程式顯示如何顯示批註節點中**批註**所參考**的工作名稱**。

#### <a name="to-display-a-property"></a>若要顯示內容

1. 開啟您在先前程式中建立的方案。

2. 將具有**屬性名稱主旨**的角色多重性設定為 0 ..1，以確定**批註**只會參考單一網域類別。 屬性名稱應該會成為**主旨，而**關聯性名稱應該會變成**CommentReferencesSubject**。

3. 在 [ **DSL Explorer**] 中，以滑鼠右鍵按一下 [ **Explorer 行為**]，然後按一下 [**加入新的 explorer 節點設定**]。

     [ **ExplorerNodeSettings** ] 節點會出現在 [**自訂節點設定**] 節點底下。

4. 選取 [ **ExplorerNodeSettings**]，然後在 [**屬性**] 視窗中，將 [**類別**] 設定為 [**批註**]。

5. 以滑鼠右鍵按一下 [**批註**] 節點，然後按一下 [**加入新屬性路徑**]。

     隨即顯示名為 [**屬性**] 的新節點。

6. 選取 [**顯示內容**]，然後在 [**屬性**] 視窗中，按一下 [ **Path To] 屬性**的 [值] 欄位。 依序選取 [**批註**]、[ **CommentReferencesSubject**] 和 [ **FlowElement**]。 產生的路徑應該類似**CommentReferencesSubject。主旨/！** 主旨。

7. 在**屬性**的 [值] 欄位中，選取 [**名稱**]。

8. 轉換所有範本，然後建立並執行您的方案。

9. 在產生的設計工具中，開啟範例圖表。

10. 在批註專案和圖表上的**Task1**元素之間繪製**批註連接器**。

     Explorer 節點應該會將批註顯示為**Task1**。

## <a name="hiding-nodes"></a>隱藏節點
 您可以在 [ **DSL explorer**] 的 [**隱藏節點**] 節點中加入節點的路徑，藉以隱藏您的瀏覽器中的節點。 下列程式顯示如何隱藏**批註**節點。

#### <a name="to-hide-an-explorer-node"></a>若要隱藏 explorer 節點

1. 開啟您在先前程式中建立的方案。

2. 在 [ **DSL Explorer**] 中，以滑鼠右鍵按一下 [ **Explorer 行為**]，然後按一下 [**加入新的網域路徑**]。

     [**網域路徑**] 節點會出現在 [**隱藏的節點**] 底下。

3. 選取 [**網域路徑**]，然後在 [**屬性**] 視窗中，按一下 [**路徑定義**] 的 [值] 欄位。 依序選取 [ **FlowGraph**] 和 [ **FlowGraphHasComments**]。 產生的路徑應該類似**FlowGraphHasComments。批註**

4. 轉換所有範本，然後建立並執行您的方案。

5. 在產生的設計工具中，開啟範例圖表。

     Explorer 應該只會顯示 [動作專案] 節點，而且不應該顯示 [**批註** **] 節點。**

## <a name="see-also"></a>另請參閱

- [Domain-Specific Language Tools Glossary](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa) (特定領域語言工具字彙表)
