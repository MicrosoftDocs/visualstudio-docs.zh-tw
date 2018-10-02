---
title: XML 結構描述對話方塊 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0271fa26-2205-49bd-96e0-ae1441571808
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9d388dc928b2f15c084034831a4b05f9d6420a65
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47487887"
---
# <a name="xml-schemas-dialog-box"></a>XML 結構描述對話方塊
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[XML 結構描述對話方塊](https://docs.microsoft.com/visualstudio/xml-tools/xml-schemas-dialog-box)。  
  
  
**XML 結構描述**對話方塊用來選取哪一個 XML 結構描述定義語言 (XSD) 結構描述與 XML 文件產生關聯。 您可以從結構描述快取中選取結構描述，或指定快取中沒有的結構描述。 選取的結構描述會被視為結構描述集的一部分。 結構描述集用於 IntelliSense 以及 XML 文件驗證。  
  
 您可以存取**XML 結構描述**對話方塊中，按一下**結構描述**按鈕，在 [文件屬性] 視窗中，或選取**結構描述**從**XML**功能表。  
  
## <a name="uielement-list"></a>UIElement 清單  
 **使用**  
 選取如何使用 XML 結構描述。  
  
-   **自動**。 目前的文件沒有使用這個結構描述，但是可用於自動關聯。 如果 XML 文件宣告符合此結構描述之 `targetNamespace` 的命名空間，將會自動關聯該結構描述，而且會包含在結構描述集中。  
  
-   **使用此結構描述**。 此結構描述正由目前的文件所使用。 使用者已經明確要求藉由按一下此結構描述來使用該結構描述，或者讓結構描述根據相符的 `targetNamespace` 自動關聯。  
  
-   **請勿使用選取的結構描述**。 即使結構描述擁有相符的 `targetNamespace`，目前的文件也不會使用此結構描述。 在結構描述快取或方案中有一個以上相同結構描述的版本時，這個設定對於解決衝突可能很實用。  
  
 **目標命名空間**  
 顯示與 XML 結構描述相關聯的目標命名空間。  
  
 **檔案名稱**  
 顯示 XML 結構描述檔案名稱。  
  
 **[新增]**  
 會開啟**開啟 XSD 結構描述**對話方塊，可讓您選取要加入至結構描述集合的其他結構描述。 當您將結構描述加入結構描述設定，請**使用**資料行值設定為**使用這個結構描述**。  
  
 **移除**  
 從結構描述集移除目前選取的結構描述。 這樣會從記憶體中的結構描述快取 (但不會從檔案系統) 移除結構描述。  
  
## <a name="see-also"></a>另請參閱  
 [XML 編輯器元件](../xml-tools/xml-editor-components.md)   
 [如何： 選取要使用的 XML 結構描述](../xml-tools/how-to-select-the-xml-schemas-to-use.md)   
 [結構描述快取](../xml-tools/schema-cache.md)



