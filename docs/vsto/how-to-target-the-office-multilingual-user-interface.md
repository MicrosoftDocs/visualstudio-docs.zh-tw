---
title: HOW TO：目標的 Office 多語系使用者介面
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- globalization [Office development in Visual Studio], user interface targeting
- MUI [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], localization
- Multilingual User Interface [Office development in Visual Studio]
- localization [Office development in Visual Studio], user interface targeting
- Office applications [Office development in Visual Studio], globalization
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5180780835f36768cef77207189a1346c1dccdca
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2019
ms.locfileid: "54866508"
---
# <a name="how-to-target-the-office-multilingual-user-interface"></a>HOW TO：目標的 Office 多語系使用者介面
  多語系使用者介面 (MUI) 是一種 Microsoft Office 的功能，讓使用者能夠變更的使用者介面 (UI) 語言。 比方說，使用英文的 UI 終端使用者可以變更 UI 的語言為西班牙文。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 如果您的應用程式將由誰使用許多語言的 Office，您可以新增程式碼，以自動 UI 字串以符合 Office 所使用的使用者的電腦上 （如果使用者已安裝正確的資源） 的語言的語言。  
  
## <a name="to-check-the-current-office-ui-setting"></a>若要檢查目前的 Office UI 設定  
  
1.  使用<xref:System.Threading.Thread.CurrentUICulture%2A>屬性目前的執行緒。 設定您的 UI 字串，以符合目前使用者的電腦執行的 Office 版本所使用的語言的語言。  
  
     [!code-vb[Trin_VstcoreCreatingExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/Sheet1.vb#10)]
     [!code-csharp[Trin_VstcoreCreatingExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/Sheet1.cs#10)]  
  
## <a name="see-also"></a>另請參閱  
 [如何：透過主要 interop 組件的目標 Office 應用程式](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)   
 [在 Office 方案中的晚期繫結](../vsto/late-binding-in-office-solutions.md)  
