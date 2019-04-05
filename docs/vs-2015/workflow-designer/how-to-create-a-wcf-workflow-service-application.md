---
title: HOW TO：建立 WCF 工作流程服務應用程式 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 12d675ac-27d8-4d86-ba16-6f7688f8c841
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0e7bf54f527a82bb59a8dc9248d3d9294a07aa59
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58938930"
---
# <a name="how-to-create-a-wcf-workflow-service-application"></a>HOW TO：建立 WCF 工作流程服務應用程式
[!INCLUDE[indigo1](../includes/indigo1-md.md)] 工作流程服務應用程式是分散式通訊服務，可在用戶端與服務本身之間傳遞訊息，並跨越處理序界限。 服務端的服務合約實作是採用類似 .NET Framework 3.5 舊版工作流程服務的方式，透過 [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] 中的工作流程活動來宣告完成。  
  
### <a name="to-create-a-wcf-workflow-service-application"></a>若要建立 WCF 工作流程服務應用程式  
  
1.  啟動 [!INCLUDE[vs2010](../includes/vs2010-md.md)]。  
  
2.  在 **檔案**功能表上，指向**新增**，然後選取 **專案...**.  
  
     [ **新增專案** ] 對話方塊隨即開啟。  
  
3.  在 **已安裝的範本**窗格中，選取**WCF**或是**工作流程**從**Visual C#** 或**Visual Basic**視您選擇的語言而定的群組。  
  
4.  在中間窗格中，選取**WCF 工作流程服務應用程式**。  
  
5.  在 **名稱**方塊中，輸入您的專案，讓您輕鬆地識別的描述性名稱。  
  
6.  在 **位置**方塊中，輸入您要儲存您的專案，或按一下 的目錄**瀏覽**來巡覽找到它。  
  
7.  在 **解決方案**方塊中，選取 建立新的方案，，然後按一下**確定**。  
  
    > [!NOTE]
    >  如果您想要新增至現有的方案工作流程主控台應用程式，開啟該方案中的[!INCLUDE[vs2010](../includes/vs2010-md.md)]，以滑鼠右鍵按一下方案中的**方案總管 中**，然後選取**新增**，然後**新增專案...** 若要開啟 [**新的專案**] 對話方塊。 依照本程序上面的說明繼續進行。  
  
8.  專案範本會以 XAML 格式建立服務定義。 [!INCLUDE[wfd1](../includes/wfd1-md.md)] 會開啟設計檢視，其中有包含一組 <xref:System.Activities.Statements.Sequence> 和 <xref:System.ServiceModel.Activities.Receive> 活動的 <xref:System.ServiceModel.Activities.SendReply> 活動。  
  
## <a name="see-also"></a>另請參閱  
 [如何：建立活動](http://msdn.microsoft.com/library/c09b1e99-21b5-4d96-9c04-ec31db3f4436)   
 [建立工作流程專案](../workflow-designer/creating-a-workflow-project.md)