---
title: 如何： 以程式設計方式搜尋特定連絡人 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- contacts [Office development in Visual Studio], searching
- searching contacts
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6799041283fab154be40233729dd3c14b1978ed9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-programmatically-search-for-a-specific-contact"></a>如何：以程式設計方式搜尋特定的連絡人
  下列範例會在 Outlook 的 [連絡人] 資料夾中，先依名字再依姓氏來搜尋特定連絡人。 該範例假設 [連絡人] 資料夾中有名為 **John Evans** 的連絡人。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="example"></a>範例  
 [!code-csharp[Trin_Outlook_RL_SearchForContact#1](../vsto/codesnippet/CSharp/trin_outlook_rl_searchforcontact/thisaddin.cs#1)]
 [!code-vb[Trin_Outlook_RL_SearchForContact#1](../vsto/codesnippet/VisualBasic/trin_outlook_rl_searchforcontact/thisaddin.vb#1)]  
  
## <a name="see-also"></a>另請參閱  
 [使用連絡人項目](../vsto/working-with-contact-items.md)   
 [VSTO 增益集程式設計入門](../vsto/getting-started-programming-vsto-add-ins.md)  
  
  