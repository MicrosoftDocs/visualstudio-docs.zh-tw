---
title: "工具使用者介面的特定領域語言的概觀 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.dsltools.dsldesigner.editor
helpviewer_keywords: Domain-Specific Language Tools, user interface
ms.assetid: 81ae6b35-6819-41d0-953b-6b4ed81f9227
caps.latest.revision: "25"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: d76ed4d14e7333678fcf927dfa1b2f21d8573be5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2017
---
# <a name="overview-of-the-domain-specific-language-tools-user-interface"></a>Domain-Specific Language Tools 使用者介面概觀
當您第一次開啟中的特定領域語言工具 （DSL 工具） 解決方案[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，使用者介面會類似下列圖片。  
  
 ![dsl 設計工具](../modeling/media/dsl_designer.png "dsl_designer")  
  
 下表說明如何使用的使用者介面的部分。  
  
|**目**|**定義**|  
|-----------------|--------------------|  
|圖表|此圖表會顯示網域模型。<br /><br /> 圖表有兩個邊。 某一端在您的模型中定義項目類型。 在另一端定義您的模型顯示在螢幕上的方式。|  
|工具箱|拖曳工具從 [工具箱] 加入網域類別和圖形到圖表中的類型。 若要加入關聯性、 連接器和圖形地圖，按一下工具]，然後按一下 [在圖表上的來源節點，然後目標節點。|  
|DSL 總管|**DSL 總管**DSL 定義為使用中視窗時顯示。 它會顯示為樹狀結構的 DSL。 DSL 總管可讓您編輯的模型不會顯示在圖表的功能。 比方說，您可以將工具箱項目，並使用驗證程序上切換**DSL 總管**。|  
|DSL 詳細資料視窗|**DSL 詳細資料** 視窗會顯示網域的內容模型的項目可讓您控制如何顯示項目，以及如何複製及刪除項目。<br /><br /> -根據預設， **DSL 詳細資料**視窗旁會顯示**錯誤清單**和**輸出**windows。|  
  
## <a name="the-domain-model-diagram"></a>網域模型圖表  
 網域模型圖分成兩個部分。 之一端中的圖表會顯示模型中的項目和關聯性。 在另一端會示範如何在模型顯示，並包含用來顯示項目和屬性的模型圖表的圖形。 下圖顯示圖表項的目。  
  
 ![具有泳道的 dsl 設計工具](../modeling/media/dsl_desinger.png "dsl_desinger")  
  
 下表說明一些網域模型圖表的項目。  
  
|**詞彙**|**定義**|  
|--------------|--------------------|  
|領域類別|網域類別是您的模型中的項目類型。<br /><br /> 領域類別可以出現一次在圖表中，如果它是一個以上的關聯性的目標。<br /><br /> 若要加入網域類別，將從網域類別工具拖曳**工具箱**至**類別和關聯性**圖表的側邊。|  
|網域關聯性|網域關聯性是您的模型中的項目之間的連結類型。<br /><br /> *內嵌關聯性*指出目標項目是擁有或包含的來源項目，而且會以實線。 在模型中的每個項目應該是一個內嵌關聯性的目標，讓模型形成樹狀結構。 A*參考關聯性*指示一般的連結模型項目，並會顯示為虛線。 任何項目可以有任意數目的參考連結。<br /><br /> 此工具，即可建立關聯性**工具箱**、 來源網域類別，然後按一下 目標類別。|  
|圖形與連接器|圖形指定模型項目應如何顯示 DSL 圖表。，連接器指定行上可以用來顯示關聯性的 DSL 圖表。<br /><br /> 若要建立圖形或連接器，將工具拖曳至**圖表項目**圖表的側邊。|  
|圖形對應|圖形地圖會顯示為的網域模型圖表中，它會顯示網域類別連結圖形或連接器，它會顯示的網域關聯性。|  
  
## <a name="see-also"></a>另請參閱  
 [特定領域語言工具的概觀](../modeling/overview-of-domain-specific-language-tools.md)   
 [特定領域語言工具詞彙](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)   
 [自訂及擴充特定領域語言](../modeling/customizing-and-extending-a-domain-specific-language.md)