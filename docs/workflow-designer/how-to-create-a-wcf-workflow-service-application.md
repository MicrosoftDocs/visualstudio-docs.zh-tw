---
title: 工作流程設計工具-如何： 建立 WCF 工作流程服務應用程式
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: 12d675ac-27d8-4d86-ba16-6f7688f8c841
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 93fb69862c228a3b6e61467facba188dd20c67c7
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-a-wcf-workflow-service-application"></a>HOW TO：建立 WCF 工作流程服務應用程式

Windows Communication Foundation (WCF) 工作流程服務應用程式是分散式的通訊服務，用戶端和本身之間傳遞訊息的跨處理序界限。 在服務端的服務合約的實作是以宣告方式透過.NET Framework 4 中的工作流程活動，類似於.NET Framework 3.5 舊版工作流程服務的方式。

## <a name="to-create-a-wcf-workflow-service-application"></a>若要建立 WCF 工作流程服務應用程式

1.  啟動 Visual Studio 2010。

2.  在 [檔案] 功能表上，指向 [新增]，然後選取 [專案]。

     [ **新增專案** ] 對話方塊隨即開啟。

3.  在**已安裝的範本**窗格中，選取**WCF**或**工作流程**從其中**Visual C#** 或**Visual Basic**分組根據您所選擇的語言。

4.  在中間窗格中，選取**WCF 工作流程服務應用程式**。

5.  在**名稱**方塊中，輸入您的專案讓您輕鬆識別的描述性名稱。

6.  在**位置**方塊中，輸入您要儲存您的專案，或按一下的目錄**瀏覽**來巡覽找到它。

7.  在**方案**方塊中，選取 建立新的方案，然後按一下**確定**。

    > [!NOTE]
    > 如果您想要新增至現有的方案工作流程主控台應用程式，在 Visual Studio 2010 中開啟該方案，以滑鼠右鍵按一下方案中的**方案總管 中**，然後選取**新增**，然後**新的專案**開啟**新專案** 對話方塊。 依照本程序上面的說明繼續進行。

8.  專案範本會以 XAML 格式建立服務定義。 Windows 工作流程設計工具會開啟至 [設計] 檢視<xref:System.Activities.Statements.Sequence>活動，其中包含一組<xref:System.ServiceModel.Activities.Receive>和<xref:System.ServiceModel.Activities.SendReply>活動。

## <a name="see-also"></a>另請參閱

- [如何：建立活動](/dotnet/framework/windows-workflow-foundation/how-to-create-an-activity)
- [建立工作流程專案](../workflow-designer/creating-a-workflow-project.md)