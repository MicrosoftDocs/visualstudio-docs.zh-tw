---
title: 如何： 檢查使用內容模型檢視節點的內容模型 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c42ddac8-b0e3-48d6-9832-112a19d6c104
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 25e47eed752a78caebcbae66a527cc847ac7d8f7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47485222"
---
# <a name="how-to-examine-the-content-model-of-nodes-using-the-content-model-view"></a>HOW TO：使用內容模型檢視檢查節點的內容模型
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[如何： 檢查內容模型的節點使用內容模型檢視](https://docs.microsoft.com/visualstudio/xml-tools/how-to-examine-the-content-model-of-nodes-using-the-content-model-view)。  
  
  
本主題描述如何瀏覽您使用的節點[內容模型檢視](../xml-tools/content-model-view.md)。  
  
### <a name="to-create-a-new-xsd-file-and-display-the-root-element-in-the-content-model-view"></a>建立新的 XSD 檔案，並且在內容模型檢視中顯示根項目  
  
1.  建立新的 XML 結構描述檔案。  
  
2.  按一下 **使用 XML 編輯器檢視與編輯基礎 XML 結構描述檔案**開始檢視上。  
  
3.  XML 結構描述範例程式碼複製[範例 XML 結構描述： 採購單結構描述](../xml-tools/sample-xsd-file-purchase-order-schema.md)並貼上取代預設新增至新 XSD 檔案的程式碼。  
  
4.  選取 `purchaseOrder`項目在結構描述總管 中，以滑鼠右鍵按一下`purchaseOrder`項目在 XML 編輯器 中，然後選取**在 XML 總管中顯示**。  
  
5.  以滑鼠右鍵按一下`purchaseOrder`XML 總管，然後選取**在內容模型檢視中顯示**。  
  
     內容模型檢視的設計介面上會顯示 `purchaseOrder` 項目。  
  
6.  在每個節點上按兩下，或按一下每個節點右邊的雙箭頭，展開 `shipTo`、`billTo` 和 `items` 節點。  
  
     `purchaseOrder` 項目的節點已展開，您可以查看該項目的內容模型。  
  
7.  按一下 `purchaseOrder` 項目下的任何節點並查看階層連結列，以查看所選節點在結構描述集中的位置。  
  
8.  按一下 **顯示的文件**XSD 工具列切換文件中的按鈕。 您也可以以滑鼠右鍵按一下設計介面來切換文件。  
  
9. 滑鼠右鍵按一下`purchaseOrder`節點，然後選取**產生範例 XML**查看 XML 執行個體文件。



