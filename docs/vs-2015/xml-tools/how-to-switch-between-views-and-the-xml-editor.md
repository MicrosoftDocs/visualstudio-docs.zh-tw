---
title: HOW TO：檢視與 XML 編輯器之間切換 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: cb69fbbd-d99c-439e-9498-5df9050f8df0
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 55481b5f91e0bb83241a04d61d1bfa91657b5c0d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58929990"
---
# <a name="how-to-switch-between-views-and-the-xml-editor"></a>HOW TO：在檢視與 XML 編輯器之間切換
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
本主題示範如何在 XML 結構描述設計工具 (XSD 設計工具) 檢視和 XML 編輯器之間切換。 這個範例會使用[採購單結構描述](../xml-tools/sample-xsd-file-simple-schema.md)。  
  
### <a name="to-switch-between-the-views-and-the-xml-editor"></a>在檢視與 XML 編輯器之間切換  
  
1.  若要建立和編輯新的 XML 結構描述檔案，遵循[How to:建立和編輯 XSD 結構描述檔案](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md)。  
  
2.  若要從 XML 編輯器中切換 XML 結構描述設計工具中，以滑鼠右鍵按一下任何地方在 XML 編輯器 中，然後選取**檢視表設計工具**。  
  
3.  若要切換至 [圖表] 檢視使用浮水印，請按一下**使用 [圖形] 檢視查看節點之間的關聯性**開始檢視上的連結。  
  
4.  將 XML 結構描述總管中的 `USAddress` 節點拖曳到圖表檢視上。 以滑鼠右鍵按一下`USAddress`節點中的圖形檢視，然後選取**在內容模型檢視中顯示**操作功能表中。  
  
     內容模型檢視隨即出現，其中包含 `USAddress` 節點的詳細資訊。  
  
5.  若要使用工具列從內容模型檢視切換至開始檢視，請按一下 XSD 工具列上的開始檢視按鈕。  
  
6.  若要使用快速鍵切換檢視，按 CTRL+1 可切換至開始檢視、按 CTRL+2 可切換至圖表檢視，按 CTRL+3 則可切換至內容模型檢視。  
  
7.  若要移至 XML 編輯器中，從內容模型檢視，以滑鼠右鍵按一下節點，然後選取**檢視程式碼**操作功能表中。
