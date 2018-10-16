---
title: 如何： 變更圖形診斷播放電腦 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1b9aa3ea-29a0-4e21-bc57-936f33537b5c
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 327dd9c14c4bbfe2b5c37cbe26823d8bd02c76ed
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49274465"
---
# <a name="how-to-change-the-graphics-diagnostics-playback-machine"></a>如何：變更圖形診斷播放電腦
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以播放圖形資訊使用本機電腦，或使用遠端電腦或裝置。  
  
## <a name="choosing-a-playback-machine"></a>選擇播放電腦  
 播放電腦是電腦或裝置用來播放圖形記錄檔中的圖形事件。 通常，在本機電腦是最方便的選項，但有不同的硬體或驅動程式版本比電腦擷取; 的電腦上，可能無法重現轉譯問題當發生這種情況，您可以選擇更好重現問題的遠端播放電腦，以及仍然使用您的開發電腦，進行診斷。  
  
#### <a name="to-use-the-local-machine-to-play-back-graphics-information"></a>若要使用本機電腦播放圖形資訊  
  
1.  在圖形記錄文件視窗中，選擇**播放電腦**連結。 **遠端偵錯工具連接** 對話方塊隨即出現。  
  
2.  底下**手動組態**，請在**地址**屬性中，輸入`localhost`。  
  
3.  設定**驗證模式**屬性設**無**。  
  
4.  選擇**選取** 按鈕。  
  
#### <a name="to-use-a-remote-machine-to-play-back-graphics-information"></a>若要使用遠端電腦播放圖形資訊  
  
1.  在圖形記錄文件視窗中，選擇**播放電腦**連結。 **遠端偵錯工具連接** 對話方塊隨即出現。  
  
2.  底下**手動組態**，請在**地址**屬性中，輸入 Windows 網域名稱或 IP 位址的電腦或您想要用來播放圖形資訊的裝置。  
  
3.  指定您想要用來保護播放電腦連接的授權種類。  
  
    -   對於 Windows 驗證設定**驗證模式**屬性設**Windows**。  
  
    -   不使用任何驗證，設定**驗證模式**屬性設**無**。  
  
4.  選擇**選取** 按鈕。  
  
> [!NOTE]
>  **遠端偵錯工具連接**對話方塊可能也會顯示直接連線到您的開發電腦或相同的子網路上的遠端偵錯目標。 您可以為圖形診斷播放電腦使用其中一個遠端偵錯目標而不必以手動方式加以設定。 在 [**遠端偵錯工具連接**對話方塊方塊中，選取您想要的目標然後選擇**選取**] 按鈕。  
  
## <a name="see-also"></a>另請參閱  
 [圖形記錄文件](../debugger/graphics-log-document.md)



