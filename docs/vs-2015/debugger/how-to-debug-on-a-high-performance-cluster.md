---
title: 如何： 偵錯高效能叢集 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- cluster debugging
- high-perfomance debugging
ms.assetid: a2f0eb07-840e-4f95-a1b1-9509217e5b8f
caps.latest.revision: 27
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0ce148ab317b14aad6cd1e2c48a6f9245c81df98
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47497545"
---
# <a name="how-to-debug-on-a-high-performance-cluster"></a>如何：偵錯高效能叢集
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

本主題的最新的版本可從[如何： 偵錯在高效能叢集](https://docs.microsoft.com/visualstudio/debugger/how-to-debug-on-a-high-performance-cluster)。  
  
在高效能叢集上偵錯多重處理程式類似在遠端電腦上偵錯一般程式。 但是，還是有一些其他的考量。 如需一般的遠端安裝需求，請參閱[遠端偵錯](../debugger/remote-debugging.md)。  
  
 當您在高效能叢集上偵錯時，可以使用所有可用於遠端偵錯的 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 偵錯視窗和技術。 但是，因為是由遠端偵錯，所以無法使用外部主控台視窗。  
  
 **執行緒**視窗和**處理序**視窗時進行偵錯平行應用程式特別有用。 如需如何使用這些視窗的秘訣，請參閱 <<c0> [ 如何： 使用處理序視窗](http://msdn.microsoft.com/en-us/0207ce2f-8ceb-4fe7-b2b5-4dd35b035ed7)並[如何： 使用執行緒視窗](../debugger/how-to-use-the-threads-window.md)。  
  
 下列程序顯示在高效能叢集上偵錯時特別有用的一些技術。  
  
 當偵錯平行應用程式時，可能會想要在特定執行緒、處理序或電腦上設定中斷點。 您可以建立一般的中斷點然後加入中斷點篩選條件，以進行這項動作。  
  
### <a name="to-open-the-breakpoint-filter-dialog-box"></a>若要開啟中斷點篩選條件對話方塊  
  
1.  以滑鼠右鍵按一下中斷點圖像，在來源視窗中，使用的資料**反組譯碼** 視窗中，**呼叫堆疊**視窗中，或有**中斷點**視窗。  
  
2.  在捷徑功能表，按一下 **篩選**。 此選項可能層級或在子功能表下出現在頂端**中斷點**。  
  
### <a name="to-set-a-breakpoint-on-a-specific-computer"></a>若要在特定電腦上設定中斷點  
  
1.  取得電腦名稱，從**處理序**視窗。  
  
2.  選取中斷點，然後開啟**中斷點篩選條件**在先前程序中所述的對話方塊。  
  
3.  在 [**中斷點篩選條件**] 對話方塊中，輸入：  
  
     MachineName =*yourmachinename*  
  
     若要建立更複雜的篩選條件，您可以使用 AND 運算子 `&`、OR 運算子 `||`、NOT 運算子 `!` 和括號來結合子句。  
  
4.  按一下 [確定 **Deploying Office Solutions**]。  
  
### <a name="to-set-a-breakpoint-on-a-specific-process"></a>若要在特定處理序上設定中斷點  
  
1.  取得處理序名稱或處理序 ID 編號，從**處理序**視窗。  
  
2.  選取中斷點，然後開啟**中斷點篩選條件**如第一個程序所示的對話方塊。  
  
3.  在 [**中斷點篩選條件**] 對話方塊中，輸入：  
  
     `ProcessName =`  *yourprocessname*  
  
     -或-  
  
     `ProcessID =` *yourprocessIDnumber*  
  
     若要建立更複雜的篩選條件，您可以使用 AND 運算子 `&`、OR 運算子 `||`、NOT 運算子 `!` 和括號來結合子句。  
  
4.  按一下 [確定 **Deploying Office Solutions**]。  
  
### <a name="to-set-a-breakpoint-on-a-specific-thread"></a>若要在特定執行緒上設定中斷點  
  
1.  取得執行緒名稱或執行緒 ID 編號，從**執行緒**視窗。  
  
2.  選取中斷點，然後開啟**中斷點篩選條件**對話方塊中的第一個程序中所述。  
  
3.  在 [**中斷點篩選條件**] 對話方塊中，輸入：  
  
     `ThreadName =` *yourthreadname*  
  
     -或-  
  
     `ThreadID =` *yourthreadIDnumber*  
  
     若要建立更複雜的篩選條件，您可以使用 AND 運算子 `&`、OR 運算子 `||`、NOT 運算子 `!` 和括號來結合子句。  
  
4.  按一下 [確定 **Deploying Office Solutions**]。  
  
## <a name="example"></a>範例  
 下列範例顯示如何為 `marvin` 電腦和 `fourier1` 執行緒上的中斷點建立篩選條件。  
  
```  
(MachineName = marvin) & (ThreadName = fourier1)  
```  
  
## <a name="see-also"></a>另請參閱  
 [偵錯多執行緒應用程式](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [遠端偵錯](../debugger/remote-debugging.md)   
 [如何： 使用處理序視窗](http://msdn.microsoft.com/en-us/0207ce2f-8ceb-4fe7-b2b5-4dd35b035ed7)   
 [如何： 使用執行緒視窗](../debugger/how-to-use-the-threads-window.md)   
 [執行緒和處理序](http://msdn.microsoft.com/en-us/73d87480-9af3-4d1b-baf5-397d5d876ae6)   
 [使用中斷點](../debugger/using-breakpoints.md)



