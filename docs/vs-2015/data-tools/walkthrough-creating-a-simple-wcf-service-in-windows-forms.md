---
title: 逐步解說：在 Windows Forms 中建立簡單的 WCF 服務 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
helpviewer_keywords:
- WCF, walkthrough [Visual Studio]
- WCF, Visual Studio tools for
- WCF services
- WCF services, walkthrough
ms.assetid: 5fef1a64-27a4-4f10-aa57-29023e28a2d6
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c2c5fba8914ba3b5404412c0cbc55af36fe15c21
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/17/2019
ms.locfileid: "59661034"
---
# <a name="walkthrough-creating-a-simple-wcf-service-in-windows-forms"></a>逐步解說：在 Windows Forms 中建立簡單的 WCF 服務
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本逐步解說示範如何建立簡單的 [!INCLUDE[vsindigo](../includes/vsindigo-md.md)] 服務、予以測試，然後從 Windows Forms 應用程式加以存取。  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="creating-the-service"></a>建立服務  
  
#### <a name="to-create-a-wcf-service"></a>建立 WCF 服務  
  
1.  在 [ **檔案** ] 功能表上，指向 [ **新增** ]，然後按一下 [ **專案**]。  
  
2.  在 [新增專案] 對話方塊中，展開 [Visual Basic] 或 [Visual C#] 節點，按一下 [WCF]，接著是 [WCF 服務程式庫]。 按一下 [確定] 開啟專案。  
  
     ![WCF 服務程式庫專案](../data-tools/media/wcf1.PNG "wcf1")  
  
    > [!NOTE]
    >  這樣會建立一個可進行測試和存取的工作服務。 以下兩個步驟示範如何修改預設方法以使用不同的資料類型。 在實際的應用程式中，您也會將自己的功能加入服務。  
  
3.  ![IService1 檔案](../data-tools/media/wcf2.png "wcf2")  
  
     在 [**方案總管] 中**，按兩下 IService1.vb 或 IService1.cs，並找到下列這一行：  
  
     [！ 的程式碼 csharp [WCFWalkthrough #4] (../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/iservice1 (2).cs #4)] [！ 的程式碼 vb [WCFWalkthrough #4] (../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/iservice1 (2).vb #4)]  
  
     將 `value` 參數的類型變更為 `String`：  
  
     [!code-csharp[WCFWalkthrough#1](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/iservice1.cs#1)]
     [!code-vb[WCFWalkthrough#1](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/iservice1.vb#1)]  
  
     請注意上述程式碼中的 `<OperationContract()>` 或 `[OperationContract]` 屬性。 服務所公開的所有方法都需要這些屬性。  
  
4.  ![Service1 檔案](../data-tools/media/wcf3.png "wcf3")  
  
     在 [**方案總管] 中**，按兩下 Service1.vb 或 Service1.cs，並找到下列這一行：  
  
     [！ 的程式碼 csharp [WCFWalkthrough #5] (../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/service1 (2).cs #5)] [！ 的程式碼 vb [WCFWalkthrough #5] (../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/service1 (2).vb #5)]  
  
     將 value 參數的類型變更為 `String`：  
  
     [!code-csharp[WCFWalkthrough#2](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/service1.cs#2)]
     [!code-vb[WCFWalkthrough#2](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/service1.vb#2)]  
  
## <a name="testing-the-service"></a>測試服務  
  
#### <a name="to-test-a-wcf-service"></a>測試 WCF 服務  
  
1.  按 **F5** 執行服務。 A **WCF 測試用戶端**表單將會顯示，而且它會載入服務。  
  
2.  在 [WCF 測試用戶端] 表單中，按兩下 [IService1] 下的 [GetData()] 方法。 **GetData**  索引標籤會顯示。  
  
     ![GetData&#40; &#41;方法](../data-tools/media/wcf4.png "wcf4")  
  
3.  在 [要求] 方塊中，選取 [值] 欄位，然後鍵入 `Hello`。  
  
     ![[值] 欄位](../data-tools/media/wcf5.png "wcf5")  
  
4.  按一下 [叫用] 按鈕。 如果**安全性警告**對話方塊隨即出現，請按一下**確定**。 結果會顯示在**回應** 方塊中。  
  
     ![在 [回應] 方塊的結果](../data-tools/media/wcf6.png "wcf6")  
  
5.  在 [檔案] 功能表上，按一下 [結束] 關閉測試表單。  
  
## <a name="accessing-the-service"></a>存取服務  
  
#### <a name="to-reference-a-wcf-service"></a>參考 WCF 服務  
  
1.  在 [檔案] 功能表上，指向 [新增]，然後按一下 [新增專案]。  
  
2.  在**新的專案**對話方塊方塊中，展開**Visual Basic**或**Visual C#** 節點，然後選取**Windows**，然後選取  **Windows Forms 應用程式**。 按一下 [確定] 開啟專案。  
  
     ![Windows Forms 應用程式專案](../data-tools/media/wcf7.png "wcf7")  
  
3.  以滑鼠右鍵按一下 [WindowsApplication1]，然後按一下 [新增服務參考]。 **加入服務參考**對話方塊會隨即出現。  
  
4.  在 [新增服務參考] 對話方塊中，按一下 [探索]。  
  
     ![[加入服務參考] 對話方塊](../data-tools/media/wcf8.png "wcf8")  
  
     **Service1**會顯示在**Services**窗格。  
  
5.  按一下 [確定] 新增服務參考。  
  
#### <a name="to-build-a-client-application"></a>建置用戶端應用程式  
  
1.  在 [方案總管] 中，按兩下 [Form1.vb] 或 [Form1.cs] 開啟 Windows Form 設計工具 (如果尚未開啟)。  
  
2.  從 [工具箱] 中，將 `TextBox` 控制項、`Label` 控制項及 `Button` 控制項拖曳至表單。  
  
     ![將控制項加入至表單](../data-tools/media/wcf9.png "wcf9")  
  
3.  按兩下 [`Button`]，並將下列程式碼加入 `Click` 事件處理常式：  
  
     [!code-csharp[WCFWalkthrough#3](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/form1.cs#3)]
     [!code-vb[WCFWalkthrough#3](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/form1.vb#3)]  
  
4.  在 [方案總管] 中，以滑鼠右鍵按一下 [WindowsApplication1]，然後按一下 [設定為啟始專案]。  
  
5.  按 **F5** 執行專案。 輸入一些文字，然後按一下按鈕。 標籤會顯示「您輸入：」以及您輸入的文字。  
  
     ![結果的顯示格式](../data-tools/media/wcf10.png "wcf10")  
  
## <a name="see-also"></a>另請參閱  
 [Visual Studio 中的 Windows Communication Foundation 服務和 WCF 資料服務](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
