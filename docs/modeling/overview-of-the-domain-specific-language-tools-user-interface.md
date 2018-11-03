---
title: Domain-Specific Language Tools 使用者介面概觀
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.editor
helpviewer_keywords:
- Domain-Specific Language Tools, user interface
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: d54ba969e06f3bd951556f8d8f347977419fc015
ms.sourcegitcommit: 768d7877fe826737bafdac6c94c43ef70bf45076
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2018
ms.locfileid: "50966488"
---
# <a name="overview-of-the-domain-specific-language-tools-user-interface"></a>Domain-Specific Language Tools 使用者介面概觀
當您第一次開啟特定領域語言工具 （DSL 工具） 方案在 Visual Studio 中時，使用者介面將類似下列圖片。

 ![dsl 設計工具](../modeling/media/dsl_designer.png)

 下表說明如何使用 UI 的部分。

|**目**|**定義**|
|-|-|
|圖表|此圖表會顯示在領域模型。<br /><br /> 圖表有兩個邊。 某一端在您的模型中定義項目類型。 另一端會定義您的模型會出現在螢幕上的方式。|
|工具箱|拖曳工具從 [工具箱] 加入網域類別和圖形至圖表的類型。 若要新增關聯性、 連接器和圖形對應，請按一下工具]，然後按一下 [在圖表上的 [來源] 節點，然後在目標節點。|
|DSL 總管|**DSL 總管 中**DSL 定義使用中視窗時，隨即出現。 它會顯示為樹狀結構的 DSL。 DSL 總管 可讓您編輯的模型不會顯示在圖表的功能。 例如，您可以在 [新增工具箱項目，並使用驗證程序上切換**DSL explorer]**。|
|DSL 詳細資料視窗|**DSL 詳細資料**視窗會顯示定義域的屬性可讓您控制如何顯示項目，以及如何複製及刪除項目模型的項目。<br /><br /> -根據預設， **DSL 詳細資料** 視窗旁邊會出現**錯誤清單**並**輸出**windows。|

## <a name="the-domain-model-diagram"></a>網域模型圖表
 網域模型圖分成兩個部分。 圖表的一方會顯示模型中的項目和關聯性。 另一端會示範如何在模型顯示，並包含用來顯示項目和屬性的模型圖表的圖形。 下圖顯示圖表項的目。

 ![具有泳道的 dsl 設計工具](../modeling/media/dsl_desinger.png)

 下表說明一些網域模型圖表的項目。

|**詞彙**|**定義**|
|-|-|
|網域類別|網域類別是在您的模型中的項目類型。<br /><br /> 網域類別可以出現一次在圖中，如果它是一個以上的關聯性的目標。<br /><br /> 若要加入的網域類別，將網域類別工具從拖曳**工具箱**要**類別和關聯性**圖表的側邊。|
|網域關聯性|網域關聯性是在您的模型中的項目之間的連結類型。<br /><br /> *內嵌關聯性*表示目標項目是擁有或包含的來源項目，並且會顯示為一條實線。 在模型中的每個項目應該是一個內嵌關聯性的目標，以便模型會形成樹狀結構。 A*參考關聯性*指出一般模型項目之間連結，並且會顯示為虛線。 任何項目可以有任意數目的參考連結。<br /><br /> 此工具，即可建立關聯性**工具箱**，按一下 來源網域類別，然後按一下 目標類別。|
|圖形與連接器|圖形可讓您指定模型項目應該如何顯示在 DSL 圖表。，連接器可用來顯示關聯性的 DSL 圖表上指定行。<br /><br /> 若要建立圖形或連接器，將工具拖曳至**圖表項目**圖表的側邊。|
|圖形對應|圖形對應會顯示為的網域模型圖中，將圖形連結至網域類別，它會顯示，或連接至它所顯示的網域關聯性的連接器。|

## <a name="see-also"></a>另請參閱

- [特定領域語言工具概觀](../modeling/overview-of-domain-specific-language-tools.md)
- [特定領域語言工具字彙](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
- [自訂及擴充特定領域語言](../modeling/customizing-and-extending-a-domain-specific-language.md)