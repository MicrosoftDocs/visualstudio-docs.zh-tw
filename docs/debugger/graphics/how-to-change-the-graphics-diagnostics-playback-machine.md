---
title: 如何：變更圖形診斷播放電腦 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 1b9aa3ea-29a0-4e21-bc57-936f33537b5c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4f057e2e4f9d39fd3c5d985b3f0d19751d508614
ms.sourcegitcommit: f27084e64c79e6428746a20dda92795df996fb31
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85769380"
---
# <a name="how-to-change-the-graphics-diagnostics-playback-machine"></a>如何：變更圖形診斷播放電腦
您可以使用本機電腦或使用遠端電腦或裝置來播放圖形資訊。

## <a name="choosing-a-playback-machine"></a>選擇播放電腦
 播放電腦是用來從圖形記錄播放圖形事件的電腦或裝置。 通常，本機電腦是最方便的選項，但是轉譯問題可能不會在具有不同硬體或驅動程式版本的電腦上重現，而不會在其被攔截的電腦上重新產生;發生這種情況時，您可以選擇較佳的遠端播放電腦來重現問題，並繼續使用您的開發電腦來進行診斷。

#### <a name="to-use-the-local-machine-to-play-back-graphics-information"></a>使用本機電腦播放圖形資訊

1. 在 [圖形記錄檔] 視窗中，選擇 [**播放電腦**] 連結。 [**遠端偵錯程式連接**] 對話方塊隨即出現。

2. 在 [**手動**設定] 下的 [**位址**] 屬性中，輸入 `localhost` 。

3. 將 [**驗證模式]** 屬性設定為 [**無**]。

4. 選擇 [選取]**** 按鈕。

#### <a name="to-use-a-remote-machine-to-play-back-graphics-information"></a>使用遠端電腦播放圖形資訊

1. 在 [圖形記錄檔] 視窗中，選擇 [**播放電腦**] 連結。 [**遠端偵錯程式連接**] 對話方塊隨即出現。

2. 在 [**手動**設定] 下的 [**位址**] 屬性中，輸入您要用來播放圖形資訊之電腦或裝置的 Windows 功能變數名稱或 IP 位址。

3. 指定您想要用來保護播放電腦連線的授權類型。

    - 若為 Windows 驗證，請將 [**驗證模式]** 屬性設定為 [ **windows**]。

    - 若不進行驗證，請將 [**驗證模式]** 屬性設定為 [**無**]。

4. 選擇 [選取]**** 按鈕。

> [!NOTE]
> [**遠端偵錯程式連接**] 對話方塊也可能會顯示直接連接到您的開發電腦或位於相同子網上的遠端偵錯程式目標。 您可以使用其中一個遠端偵錯的目標，做為圖形診斷播放電腦，而不需要手動設定。 在 [**遠端偵錯程式連接**] 對話方塊中，選取您要的目標，然後選擇 [**選取**] 按鈕。

## <a name="see-also"></a>另請參閱
- [圖形記錄文件](graphics-log-document.md)