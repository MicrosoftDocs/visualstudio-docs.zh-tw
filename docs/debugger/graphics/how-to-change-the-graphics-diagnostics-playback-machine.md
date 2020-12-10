---
title: 變更圖形診斷播放電腦
description: 使用您的本機電腦，或使用更能重現問題的遠端電腦或裝置，從圖形記錄播放圖形資訊。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 1b9aa3ea-29a0-4e21-bc57-936f33537b5c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8b6ae19fde7397b97ebe087557d71a52303605ec
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "96995066"
---
# <a name="how-to-change-the-graphics-diagnostics-playback-machine"></a>作法：變更圖形診斷播放電腦
您可以使用本機電腦，或使用遠端電腦或裝置來播放圖形資訊。

## <a name="choosing-a-playback-machine"></a>選擇播放電腦
 播放電腦是用來從圖形記錄播放圖形事件的電腦或裝置。 本機電腦通常是最方便的選項，但是轉譯問題可能不會在具有不同硬體或驅動程式版本的電腦上重現，而不是在它的電腦上執行;發生這種情況時，您可以選擇更能重現問題的遠端播放電腦，但仍會使用您的開發電腦來進行診斷。

#### <a name="to-use-the-local-machine-to-play-back-graphics-information"></a>使用本機電腦播放圖形資訊

1. 在 [圖形記錄檔] 視窗中，選擇 [ **播放電腦** ] 連結。 [ **遠端偵錯程式連接** ] 對話方塊隨即出現。

2. 在 [ **手動** 設定] 下的 [ **位址** ] 屬性中，輸入 `localhost` 。

3. 將 [ **驗證模式]** 屬性設定為 [ **無**]。

4. 選擇 [選取] 按鈕。

#### <a name="to-use-a-remote-machine-to-play-back-graphics-information"></a>使用遠端電腦播放圖形資訊

1. 在 [圖形記錄檔] 視窗中，選擇 [ **播放電腦** ] 連結。 [ **遠端偵錯程式連接** ] 對話方塊隨即出現。

2. 在 [ **手動** 設定] 下的 [ **位址** ] 屬性中，輸入您要用來播放圖形資訊的電腦或裝置的 Windows 功能變數名稱或 IP 位址。

3. 指定您想要用來保護播放電腦連接的授權類型。

    - 若為 Windows 驗證，請將 [ **驗證模式]** 屬性設定為 [ **windows**]。

    - 若未驗證，請將 [ **驗證模式]** 屬性設定為 [ **無**]。

4. 選擇 [選取] 按鈕。

> [!NOTE]
> [ **遠端偵錯程式連接** ] 對話方塊也可能會顯示直接連接到您的開發電腦或位於相同子網上的遠端偵錯程式目標。 您可以使用其中一個遠端偵錯程式目標作為圖形診斷播放機器，而不需要手動設定。 在 [ **遠端偵錯程式連接** ] 對話方塊中，選取您要的目標，然後選擇 [ **選取** ] 按鈕。

## <a name="see-also"></a>另請參閱
- [圖形記錄文件](graphics-log-document.md)