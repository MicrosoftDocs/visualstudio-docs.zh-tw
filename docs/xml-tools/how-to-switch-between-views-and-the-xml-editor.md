---
title: HOW TO：在檢視與 XML 編輯器之間切換
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: cb69fbbd-d99c-439e-9498-5df9050f8df0
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 09ad752dc87ea322396d6e6513593d71a7554b98
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53936239"
---
# <a name="how-to-switch-between-views-and-the-xml-editor"></a>HOW TO：檢視和 XML 編輯器之間切換

本主題示範如何在 XML 結構描述設計工具 (XSD 設計工具) 檢視和 XML 編輯器之間切換。 這個範例會使用[採購單結構描述](../xml-tools/sample-xsd-file-simple-schema.md)。

## <a name="to-switch-between-the-views-and-the-xml-editor"></a>在檢視與 XML 編輯器之間切換

1.  若要建立和編輯新的 XML 結構描述檔案，遵循[How to:建立和編輯 XSD 結構描述檔案](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md)。

2.  若要從 XML 編輯器中切換 XML 結構描述設計工具中，以滑鼠右鍵按一下 XML 編輯器中，然後選取**檢視表設計工具**。

3.  若要切換至 [圖表] 檢視使用浮水印，請按一下**使用 [圖形] 檢視查看節點之間的關聯性**開始檢視上的連結。

4.  拖曳`USAddress`節點，從**XML 結構描述總管**拖曳至圖表檢視。 以滑鼠右鍵按一下`USAddress`節點中的圖形檢視，然後選取**在內容模型檢視中顯示**操作功能表中。

     內容模型檢視隨即出現，其中包含 `USAddress` 節點的詳細資訊。

5.  若要從使用工具列的內容模型檢視切換至開始檢視，按一下**開始檢視**XSD 工具列上的按鈕。

6.  若要使用快速鍵檢視之間切換，請按**Ctrl**+**1** [啟動] 檢視中，針對**Ctrl**+**2**針對 [圖表] 檢視中，並**Ctrl**+**3**內容模型檢視。

7.  若要移至 XML 編輯器中，從內容模型檢視，以滑鼠右鍵按一下節點，然後選取**檢視程式碼**操作功能表中。