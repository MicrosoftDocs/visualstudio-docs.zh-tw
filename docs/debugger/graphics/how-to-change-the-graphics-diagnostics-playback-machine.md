---
title: 如何： 變更圖形診斷播放電腦 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 1b9aa3ea-29a0-4e21-bc57-936f33537b5c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 143ae65b8d7db584546c250bf5d032450bf220aa
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
ms.locfileid: "31473867"
---
# <a name="how-to-change-the-graphics-diagnostics-playback-machine"></a>如何：變更圖形診斷播放電腦
您可以播放圖形資訊使用本機電腦，或使用遠端電腦或裝置。  
  
## <a name="choosing-a-playback-machine"></a>選擇播放電腦  
 播放電腦是電腦或裝置用來播放圖形記錄檔中的圖形事件。 通常，在本機電腦是最方便的選項，但可能不會再它未擷取其中; 具有不同的硬體或驅動程式版本比電腦的電腦上出現的呈現問題當發生這種情況，您可以選擇更會重現問題的遠端播放電腦，然後仍然使用您的開發電腦進行診斷。  
  
#### <a name="to-use-the-local-machine-to-play-back-graphics-information"></a>若要使用本機電腦來播放圖形資訊  
  
1.  在圖形記錄文件視窗中，選擇 **播放電腦**連結。 **遠端偵錯工具連接** 對話方塊隨即出現。  
  
2.  在下**手動設定**，請在**位址**屬性中，輸入`localhost`。  
  
3.  設定**驗證模式**屬性**無**。  
  
4.  選擇**選取** 按鈕。  
  
#### <a name="to-use-a-remote-machine-to-play-back-graphics-information"></a>若要使用遠端電腦來播放圖形資訊  
  
1.  在圖形記錄文件視窗中，選擇 **播放電腦**連結。 **遠端偵錯工具連接** 對話方塊隨即出現。  
  
2.  在下**手動設定**，請在**位址**屬性中，輸入 Windows 網域名稱或 IP 位址的電腦或裝置，您要用來播放圖形資訊。  
  
3.  指定您要用來保障連線安全，以播放電腦的授權類型。  
  
    -   對於 Windows 驗證，設定**驗證模式**屬性**Windows**。  
  
    -   進行任何驗證，設定**驗證模式**屬性**無**。  
  
4.  選擇**選取** 按鈕。  
  
> [!NOTE]
>  **遠端偵錯工具連接**對話方塊可能也會顯示可直接連接到您的開發電腦或相同子網路上的遠端偵錯目標。 您可以為圖形診斷播放電腦使用其中一個遠端偵錯目標而不必以手動方式加以設定。 在**遠端偵錯工具連接**對話方塊方塊中，選取您想要然後選擇的目標**選取** 按鈕。  
  
## <a name="see-also"></a>另請參閱  
 [圖形記錄文件](graphics-log-document.md)