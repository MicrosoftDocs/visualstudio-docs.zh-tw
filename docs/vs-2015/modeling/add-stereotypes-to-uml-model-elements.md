---
title: 將造型加入 UML 模型項目 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML model, stereotypes
ms.assetid: 82545252-83ce-4e11-a419-61373be75d16
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 5bba638a595a01f17e4b7e4f8269a69cb6e466a1
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "63430492"
---
# <a name="add-stereotypes-to-uml-model-elements"></a>將造型加入 UML 模型項目
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以將造型加入 UML 模型項目以對其加上註解，並提供它的特殊屬性。 若要將造型加入模型項目，則造型必須定義在設定檔中，而且必須將設定檔連結至套件，或將設定檔連結至包含模型項目的模型。 每個造型都只能加入特定種類的模型項目 (例如 UML 類別、使用案例或元件)。  
  
 例如，如果您想要定義具有 «規格» 造型的 UML 類別，則必須在連結至標準設定檔 L2 的套件或模型內建立它。  
  
 根據預設，每個模型都會連結至 UML 標準設定檔 L2 和 L3。  
  
### <a name="to-link-a-profile-to-a-model-or-a-package"></a>將設定檔連結至模型或套件  
  
1. 開啟**UML 模型總管**。 在 [**架構**功能表上，指向**Windows**，然後按一下**UML 模型總管]**。  
  
2. 找出套件或模型，其中包含您想要在設定檔中套用造型的所有項目。  
  
3. 以滑鼠右鍵按一下封裝或模型，然後按一下**屬性**。  
  
4. 在 **屬性**視窗中，將**設定檔**屬性，以包含您想要使用的造型的設定檔。  
  
     設定檔的造型現在可以在模型或套件內的所有項目上。 如果套件包含其他套件，則造型也會在其內的項目上。  
  
### <a name="to-add-stereotypes-to-model-elements-or-relationships"></a>將造型加入模型項目或關聯性  
  
1. 以滑鼠右鍵按一下模型項目或關聯性，在圖表上或在**UML 模型總管**，然後按一下**屬性**。  
  
    > [!NOTE]
    > 若要將相同的造型加入數個項目，您可以選取數個項目，然後以滑鼠右鍵按一下其中一個項目。  
  
2. 按一下 **造型**屬性，並選取您想要套用的造型。  
  
     對大部分種類的項目和關聯性而言，選取的造型會顯示在模型項目的 «＞ 形箭號» 中。  
  
    > [!NOTE]
    > 如果您看**造型**屬性，或如果您想要的造型未出現，請確認模型項目位於套件或模型，適當的設定檔連結。  
  
3. 有些造型可讓您設定模型項目其他屬性的值。 若要查看這些屬性，依序展開**造型**屬性。  
  
### <a name="to-create-model-elements-within-a-package"></a>在套件內建立模型項目  
  
1. 在 UML 類別圖中，或在建立封裝**UML 模型總管**。  
  
2. 使用下列其中一種方式，將模型項目加入套件：  
  
    - 在 UML 類別圖中，按一下項目的工具，然後按一下圖表上的套件內。  
  
         \-或-  
  
    - 在 UML 模型總管 中，以滑鼠右鍵按一下封裝，並指向**新增**，然後按一下 項目類型。  
  
         \-或-  
  
    - 在 [UML 模型總管] 中，將現有項目拖曳至套件。  
  
         \-或-  
  
    - 將圖表連結至套件，然後在圖表內建立項目。  
  
         若要這樣做，以滑鼠右鍵按一下圖表的空白部分，然後按一下**屬性**。 在 **屬性**視窗中，將**連結的套件**至您想要的套件。  
  
         所有您在圖表中建立的新項目都定義在該套件內。  
  
         您只能對某些類型的圖表執行這項作業。  
  
## <a name="see-also"></a>另請參閱  
 [定義要擴充 UML 的設定檔](../modeling/define-a-profile-to-extend-uml.md)   
 [自訂您的模型，使用設定檔和造型](../modeling/customize-your-model-with-profiles-and-stereotypes.md)   
 [定義套件和命名空間](../modeling/define-packages-and-namespaces.md)   
 [依據造型將 UML 類別上色](http://code.msdn.microsoft.com/UML-Color-Classes-by-07de2b70)
