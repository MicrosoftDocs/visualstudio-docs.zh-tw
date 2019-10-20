---
title: 如何：在視圖和 XML 編輯器之間切換 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: cb69fbbd-d99c-439e-9498-5df9050f8df0
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 28267f705dd9a747d0e3f3ac5dc2869ab7de8f6a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656311"
---
# <a name="how-to-switch-between-views-and-the-xml-editor"></a>HOW TO：在檢視與 XML 編輯器之間切換
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題示範如何在 XML 結構描述設計工具 (XSD 設計工具) 檢視和 XML 編輯器之間切換。 這個範例會使用[採購單架構](../xml-tools/sample-xsd-file-simple-schema.md)。

### <a name="to-switch-between-the-views-and-the-xml-editor"></a>在檢視與 XML 編輯器之間切換

1. 若要建立和編輯新的 XML 架構檔案，請依照[如何：建立和編輯 XSD 架構](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md)檔案中的步驟執行。

2. 若要從 XML 編輯器切換至 XML 架構設計工具，請以滑鼠右鍵按一下 XML 編輯器中的任何位置，然後選取 [ **View Designer**]。

3. 若要使用浮水印切換至圖表視圖，請按一下 [**使用圖表視圖] 查看 [開始] 視圖上 [節點間的關聯性]** 連結。

4. 將 XML 結構描述總管中的 `USAddress` 節點拖曳到圖表檢視上。 以滑鼠右鍵按一下圖形視圖中的 [`USAddress`] 節點，然後選取操作功能表中的 [**在內容模型視圖中顯示**]。

     內容模型檢視隨即出現，其中包含 `USAddress` 節點的詳細資訊。

5. 若要使用工具列從內容模型檢視切換至開始檢視，請按一下 XSD 工具列上的開始檢視按鈕。

6. 若要使用快速鍵切換檢視，按 CTRL+1 可切換至開始檢視、按 CTRL+2 可切換至圖表檢視，按 CTRL+3 則可切換至內容模型檢視。

7. 若要從內容模型視圖移至 XML 編輯器，請以滑鼠右鍵按一下節點，然後選取操作功能表中的 [**查看程式碼**]。
