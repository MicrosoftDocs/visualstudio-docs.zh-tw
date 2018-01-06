---
title: "如何： 以程式設計方式搜尋特定連絡人 |Microsoft 文件"
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
- contacts [Office development in Visual Studio], searching
- searching contacts
ms.assetid: ca17ce97-7b07-46e6-a476-34003e9cb9ad
caps.latest.revision: "25"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 00f10e8b3e1e79352080f4dffba983a1c0b485c2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-programmatically-search-for-a-specific-contact"></a>如何：以程式設計方式搜尋特定的連絡人
  下列範例會在 Outlook 的 [連絡人] 資料夾中，先依名字再依姓氏來搜尋特定連絡人。 該範例假設 [連絡人] 資料夾中有名為 **John Evans** 的連絡人。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>範例  
 [!code-csharp[Trin_Outlook_RL_SearchForContact#1](../vsto/codesnippet/CSharp/trin_outlook_rl_searchforcontact/thisaddin.cs#1)]
 [!code-vb[Trin_Outlook_RL_SearchForContact#1](../vsto/codesnippet/VisualBasic/trin_outlook_rl_searchforcontact/thisaddin.vb#1)]  
  
## <a name="see-also"></a>請參閱  
 [使用連絡人項目](../vsto/working-with-contact-items.md)   
 [VSTO 增益集程式設計入門](../vsto/getting-started-programming-vsto-add-ins.md)  
  
  