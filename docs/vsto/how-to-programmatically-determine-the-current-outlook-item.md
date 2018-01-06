---
title: "如何： 以程式設計方式判斷目前的 Outlook 項目的 |Microsoft 文件"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- mail items [Office development in Visual Studio], current
- e-mail [Office development in Visual Studio], current item
- SelectionChange event
- Outlook [Office development in Visual Studio], current item
ms.assetid: b4fb5ccd-b297-463e-9208-1fec42482531
caps.latest.revision: "28"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 112a2c1273b0087eea98736a4e47ac5de8787149
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-determine-the-current-outlook-item"></a>如何：以程式設計方式判斷目前的 Outlook 項目
  這個範例會使用 Explorer.SelectionChange 事件來顯示目前的資料夾以及某些選取的項目相關資訊的名稱。 程式碼接著會顯示選取的項目。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>範例  
 [!code-vb[Trin_OL_CurrentItem#1](../vsto/codesnippet/VisualBasic/Trin_OL_CurrentItem/thisaddin.vb#1)]
 [!code-csharp[Trin_OL_CurrentItem#1](../vsto/codesnippet/CSharp/Trin_OL_CurrentItem/thisaddin.cs#1)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   約會、 連絡人及電子郵件在 Microsoft Office Outlook 中的項目。  
  
## <a name="see-also"></a>請參閱  
 [Outlook 物件模型概觀](../vsto/outlook-object-model-overview.md)   
 [如何： 以程式設計方式擷取名稱的資料夾](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [如何：以程式設計方式搜尋特定的連絡人](../vsto/how-to-programmatically-search-for-a-specific-contact.md)  
  
  