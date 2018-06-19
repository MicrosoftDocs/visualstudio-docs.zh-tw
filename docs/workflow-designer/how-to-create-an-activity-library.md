---
title: 工作流程設計工具-如何： 建立活動程式庫
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
ms.assetid: 1eeebe74-7303-4345-8a83-fe37a26bc84b
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ef62a5098581042a4995d6c522e0757c361e9d4f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
ms.locfileid: "31974040"
---
# <a name="how-to-create-an-activity-library"></a>HOW TO：建立活動程式庫
自訂活動是用來將工作流程中特定的商務程序模型化。 Visual Studio 2010 中的活動程式庫範本會提供可讓您建立這類自訂活動，以視覺化方式使用 Windows 工作流程設計工具。

### <a name="to-create-a-workflow-activity-library"></a>若要建立工作流程活動程式庫

1.  啟動 Visual Studio 2010。

2.  在 [檔案] 功能表上，指向 [新增]，然後選取 [專案]。

     [ **新增專案** ] 對話方塊隨即開啟。

3.  在**專案類型**窗格中，選取**工作流程**從其中**Visual C#** 專案或**Visual Basic**群組取決於您語言喜好設定。

4.  在**範本**窗格中，選取**活動程式庫**。

5.  在**名稱**中，輸入您的專案的描述性名稱讓您輕鬆識別。

6.  在**位置**中，輸入您要儲存您的專案，或按一下目錄**瀏覽**來巡覽找到它。

7.  在**方案**方塊、 輸入的描述性名稱，您的方案，然後按一下 **確定**。

    > [!NOTE]
    > 如果您想要新增至現有的方案工作流程主控台應用程式，在 Visual Studio 2010 中開啟該方案，以滑鼠右鍵按一下方案中的**方案總管 中**，然後選取**新增**，然後**新的專案**開啟**新專案** 對話方塊。 依照本程序上面的說明繼續進行。

8.  專案範本會以 XAML 格式建立活動定義。 Windows 工作流程設計工具開啟，並顯示您的自訂活動的畫布。

9. 活動拖曳至**工具箱**至設計介面，以納入您的自訂活動。

    > [!CAUTION]
    > 自訂活動的主體中僅可有一個子活動，但是該子活動可以是複合活動，例如 <xref:System.Activities.Statements.Sequence> 活動或 <xref:System.Activities.Statements.Flowchart> 活動。

## <a name="see-also"></a>另請參閱

- [如何：建立活動](/dotnet/framework/windows-workflow-foundation/how-to-create-an-activity)
- [建立工作流程專案](../workflow-designer/creating-a-workflow-project.md)