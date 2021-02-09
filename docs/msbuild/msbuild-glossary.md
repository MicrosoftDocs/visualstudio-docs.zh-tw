---
title: MSBuild 字彙表
description: 瞭解 Microsoft Build Engine () 詞彙描述組建引擎及其元件的詞彙。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: f767d8e4-24d8-4803-80eb-e857202dbe2c
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e6e5ef85ffc4a10719cfbef79cbaf6dad08bdbf0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919126"
---
# <a name="msbuild-glossary"></a>MSBuild 字彙表

這些詞彙可用來說明 Microsoft Build Engine (MSBuild) 及其元件。

## <a name="assemblyfoldersex"></a>AssemblyFoldersEx

一個登錄位置，協力廠商可在其中儲存每個架構版本的路徑，而他們支援設計階段的解決方案可期望在這些架構路徑中找到參考組件。

## <a name="batching"></a>批次處理

批次處理表示會根據項目中繼資料，將項目分割成不同的類別 (稱為「批次」)，然後使用每個批次一次執行一或多個目標。 MSBuild 批次處理相當於 for 迴圈建構。 如需詳細資訊，請參閱[批次處理](../msbuild/msbuild-batching.md)。

## <a name="build-scope"></a>建置範圍

建置範圍會說明一個 MSBuild 物件 (例如，全域屬性)，而專案及多專案組建中所建立的任何子專案可能會看見此物件。

## <a name="child-project"></a>子專案

請參閱＜專案，子系＞。

## <a name="condition"></a>condition (條件)

您可以有條件地定義許多 MSBuild 項目，也就是，項目中會出現 `Condition` 屬性。 除非條件判斷值為 `true`，否則會忽略條件式項目的內容。 如需詳細資訊，請參閱[條件](../msbuild/msbuild-conditions.md)。

## <a name="definition-item"></a>定義，項目

請參閱＜項目定義＞。

## <a name="emit-item"></a>發出項目

在組建的執行階段，可以透過具有子系 `Output` 項目 (Element) (內含 `ItemName` 屬性) 的工作來建立或修改項目 (Item)。 此工作即稱為「發出」新的項目。

## <a name="emit-property"></a>發出屬性

在組建的執行階段，可以透過具有子系 `Output` 項目 (內含 `PropertyName` 屬性) 的工作來建立或修改屬性。 此工作即稱為「發出」新的屬性。

## <a name="evaluation-phase"></a>評估階段

評估是專案建置的第一個階段。 所有的屬性和項目都會以其在專案中出現的順序來評估。 匯入的專案則是在專案中遇到它們時進行評估。 目標和工作要到執行階段才會執行，而它們所宣告或發出的任何屬性或項目則會在評估期間遭到忽略。

## <a name="execution-phase"></a>執行階段

執行是專案建置的第二個階段。 此階段會建置所選取的目標並執行工作。 相較於屬性和項目的評估值，可建立或修改它們。

## <a name="function-property"></a>函式，屬性

請參閱＜屬性函式＞。

## <a name="function-item"></a>函式，項目

請參閱＜項目函式＞。

## <a name="item"></a>item

項目 (Item) 是建置系統的輸入，會根據它們的項目 (Element) 名稱分組到項目 (Item) 類型。 項目通常代表檔案。 由於項目是根據其所屬的項目類型來命名，因此可交換使用「項目」和「項目值」等詞彙。 如需詳細資訊，請參閱[項目](../msbuild/msbuild-items.md)。

## <a name="item-definition"></a>項目定義

項目定義群組包含要將預設中繼資料加入任何項目類型的項目定義。 如同已知的中繼資料，預設的中繼資料會與指定項目類型的所有項目相關聯。 您可以在項目定義中明確覆寫預設的中繼資料。 如需詳細資訊，請參閱[項目定義](../msbuild/item-definitions.md)。

## <a name="item-function"></a>項目函式

項目函式會在專案中取得項目的相關資訊。 這些函式會簡化取得 Distinct() 項目的方式，速度比執行項目迴圈還快。 有一些函式可用來管理項目路徑和字串。 如需詳細資訊，請參閱 [專案函數](../msbuild/item-functions.md)。

## <a name="item-metadata"></a>項目中繼資料

請參閱＜中繼資料，項目＞。

## <a name="item-type"></a>項目類型

項目類型是具名的項目清單，可用來做為工作的參數。 工作會使用項目值來執行建置程序的步驟。 如需詳細資訊，請參閱[項目](../msbuild/msbuild-items.md)。

## <a name="metadata-item"></a>中繼資料，項目

項目中繼資料是與項目相關聯的名稱/值組集合。 除了已知的中繼資料，中繼資料還會提供項目的描述性資訊，而且是選擇性的。 如需詳細資訊，請參閱[項目](../msbuild/msbuild-items.md)。

## <a name="metadata-well-known"></a>中繼資料，已知

已知的中繼資料是使用預先定義的值初始化的唯讀項目中繼資料。 已知的中繼資料會針對參考檔案的項目提供描述性資訊。 例如，名為 `FullPath` 的已知中繼資料值是參考檔案的完整路徑。 如需詳細資訊，請參閱[項目](../msbuild/msbuild-items.md)。

## <a name="multitargeting"></a>多目標

應用程式或組件專案能夠以來自 MSBuild 和 Visual Studio 的許多不同 CLR 和架構為目標。

## <a name="profile"></a>profile

完整架構的子集。 這可用來減少需要下載到電腦的需求量。

## <a name="project-file"></a>專案檔

專案檔包含控制組建的 MSBuild 指令碼。 專案檔的副檔名結尾通常是 *proj*，例如 *.csproj* 或 *.vbproj*。 專案檔可匯入屬性檔和目標檔案。

## <a name="property"></a>屬性

屬性是用來控制建置程序的索引鍵/值組。 如需詳細資訊，請參閱 [MSBuild 屬性](../msbuild/msbuild-properties.md)。

## <a name="property-environment"></a>屬性，環境

環境屬性是會自動初始化為具相同名稱之系統環境變數值的屬性。 如需詳細資訊，請參閱 [MSBuild 屬性](../msbuild/msbuild-properties.md)。

## <a name="property-file"></a>屬性檔

屬性檔是包含大部分屬性群組及可引導建置之項目群組的專案檔。 依照慣例，其副檔名為 *.props*。 通常會在相關聯的專案檔開始時匯入屬性檔。

## <a name="property-function"></a>屬性，函式

屬性函式是一個系統屬性或方法，可用於評估 MSBuild 指令碼。 屬性方法可用來讀取系統時間、比較字串、比對規則運算式，以及執行其他動作。 如需詳細資訊，請參閱 [Property 函式](../msbuild/property-functions.md)。

## <a name="property-function-nested"></a>屬性函式，巢狀

屬性函式可能會加以結合，以形成更複雜的函式。 例如，

 `$([MSBuild]::BitwiseAnd(32,   $([System.IO.File]::GetAttributes(tempFile))))`

如需詳細資訊，請參閱 [Property 函式](../msbuild/property-functions.md)。

## <a name="property-global"></a>屬性，全域

全域屬性是用來控制建置程序的索引鍵/值組。 您可以在命令提示字元上，或使用 [MSBuild 工作](../msbuild/msbuild-task.md)的 `Properties` 屬性來設定全域屬性，而且無法在組建的評估階段加以修改。 如需詳細資訊，請參閱 [MSBuild 屬性](../msbuild/msbuild-properties.md)。

## <a name="property-local"></a>屬性，區域

區域屬性是用來控制建置程序的索引鍵/值組。 這個詞彙只能用於區分非全域屬性的屬性。

## <a name="property-registry"></a>屬性，登錄

登錄屬性的值是使用可讀取系統登錄子機碼值的特殊語法來設定。 如需詳細資訊，請參閱 [MSBuild 屬性](../msbuild/msbuild-properties.md)。

## <a name="property-reserved"></a>屬性，已保留

保留的屬性是用來控制建置程序的索引鍵/值組。 保留的屬性會自動初始化為預先定義的值。 如需詳細資訊，請參閱 [MSBuild 屬性](../msbuild/msbuild-properties.md)。

## <a name="project-scope"></a>專案範圍

專案範圍會說明一個 MSBuild 物件 (例如，區域屬性)，此物件只能在包含專案檔以及它匯入的任何專案中看見。

## <a name="project-child"></a>專案，子系

MSBuild 工作會在專案建置期間建立子專案。 這個新的專案是專案的子系，其會包含或匯入包含 MSBuild 工作的目標專案。 除非使用 `Properties` 屬性加以修改，否則子專案會繼承父專案的全域屬性。

## <a name="redist-list"></a>可轉散發套件清單

可轉散發套件清單︰對應至指定架構的組件清單。

## <a name="reference-assembly"></a>參考組件

在設計階段用來建立應用程式的組件。 您可以從參考組件中移除實際的程式碼和私用介面，僅留下中繼資料和公用介面。

## <a name="registry-property"></a>登錄屬性

請參閱＜屬性，登錄＞。

## <a name="target"></a>目標

目標會以特殊順序將工作分組，並公開專案檔的區段做為建置程序的進入點。 如需詳細資訊，請參閱[目標](../msbuild/msbuild-targets.md)。

## <a name="target-building"></a>目標，建置

請參閱＜目標，執行＞。

## <a name="target-evaluating"></a>目標，評估

由於累加編譯的緣故，因此必須針對屬性和項目的潛在變更來分析目標。 即使會略過目標，還是必須進行這些變更。 評估目標表示會執行此分析並進行這些變更。 如需詳細資訊，請參閱累加 [組建](../msbuild/incremental-builds.md)。

## <a name="target-executing"></a>目標，執行

執行目標表示會評估該目標，並執行所有不含任何條件的工作，或其條件評估為 true 的工作。 在累加編譯期間，可能會略過或執行目標，但一律會評估它們。 如需詳細資訊，請參閱＜目標，評估＞。

## <a name="target-running"></a>目標，執行

不會執行有條件評估為 false 的目標，也就是，不會對組建產生任何影響。 執行或略過執行的目標。 在任一情況下，都會評估目標。 如需詳細資訊，請參閱＜目標，評估＞。

## <a name="target-skipping"></a>目標，略過

如果累加編譯判斷所有的輸出檔都是最新狀態，則會略過目標，也就是，會評估目標，但不會執行目標內的工作。 如需詳細資訊，請參閱＜目標，評估＞。

## <a name="target-framework-moniker"></a>目標 Framework Moniker

一個名稱，可描述架構 (例如 .NETFramwork、Silverlight 等)、版本及您希望設為目標的設定檔 (例如用戶端、伺服器等)。

## <a name="targeting-pack"></a>目標套件

特定架構隨附的組建清單，以及一組適用於該架構的參考組件。

## <a name="targets-file"></a>目標檔案

目標檔案是一個專案檔，其中包含大部分的目標及可引導組建的工作。 依照慣例，其副檔名為 *.targets*。 通常會在相關聯的專案檔結束時匯入目標檔案。

## <a name="task"></a>工作 (task)

工作是 MSBuild 專案用來執行組建作業的可執行程式碼單位。 例如，工作可能是編譯輸入檔，或是執行外部工具。 如需詳細資訊，請參閱[工作](../msbuild/msbuild-tasks.md)。

## <a name="transform"></a>Transform - 轉換

轉換是從一個項目集合到另一個的一對一轉換。 除了啟用專案來轉換項目集合，轉換還能讓目標識別其輸入和輸出之間的直接對應。 如需詳細資訊，請參閱[轉換](../msbuild/msbuild-transforms.md)。

## <a name="well-known-metadata"></a>已知的中繼資料

請參閱＜中繼資料，已知＞。

## <a name="see-also"></a>另請參閱

- [MSBuild](../msbuild/msbuild.md)
