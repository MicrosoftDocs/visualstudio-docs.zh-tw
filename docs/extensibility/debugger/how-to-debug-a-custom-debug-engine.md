---
title: 如何:調試自定義調試引擎 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, debugging
- debugging [Debugging SDK], custom debug engines
ms.assetid: df27a8d6-3938-45ff-b47f-b684e80b38a0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c79790bfc9c9cd3767a453258b8c2d340f64d029
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738583"
---
# <a name="how-to-debug-a-custom-debug-engine"></a>如何:除錯自訂除錯引擎
項目類型從<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A>方法啟動調試引擎 (DE)。 這意味著 DE[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]是在控制項目類型的實例的控制下啟動的。 但是,該[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]實例無法調試 DE。 下面的步驟允許您調試自定義 DE。

> [!NOTE]
> :在"除錯自定義除錯引擎"過程中,您必須等待 DE 啟動,然後才能附加到它。 如果在 DE 開始時出現在 DE 開頭附近放置一個消息框,則可以在此時附加,然後清除消息框以繼續。 這樣,您可以捕獲所有 DE 事件。

> [!WARNING]
> 在嘗試以下過程之前,必須安裝遠端調試。 有關詳細資訊,請參閱[遠端除錯](../../debugger/remote-debugging.md)。

## <a name="debug-a-custom-debug-engine"></a>除錯自訂除錯引擎

1. 啟動*msvsmon.exe,* 遠端除錯監視器。

2. 從*msvmon.exe*中的 **「工具**」選單中,選擇 **「選項**」以開啟 **「選項**」對話框。

3. 選擇"無身份驗證"選項,然後按一**下 "確定**"。

4. 啟動[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]的實體並打開自訂 DE 專案。

5. 啟動啟動[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]DE 的第二個實體並打開自訂專案(為了開發,這通常在安裝 VSIP 時設置的實驗註冊表配置單元中)。

6. 在 這第[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]二 個實例中,從自定義專案載入源檔,然後啟動要調試的程式。 等待片刻以允許 DE 載入,或等待,直到斷點被擊中。

7. 在[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)](使用 DE 專案)的第一個實例中,從**調試**功能表中選擇 **「附加到行程**」。。

8. 在 **'附加到行程'** 對話框中,更改'**傳輸**到**遠端"(僅本機,沒有身份驗證)。**

9. 將**限定符**更改為計算機的名稱(注意:有條目的歷史記錄,因此只需鍵入此名稱一次)。

10. 在 **"可用行程'** 清單中,選擇正在執行的 DE 實體,然後單擊「**附加」** 按鈕。

11. 在 DE 中載入符號後,在 DE 代碼中放置斷點。

12. 每次停止並重新啟動調試過程時,請重複步驟 6 到 10。

## <a name="debug-a-custom-project-type"></a>除錯自訂項目型態

1. 從[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]普通註冊表配置單元開始並載入專案類型專案(這是專案類型的源,而不是專案類型的實例化)。

2. 打開項目屬性並轉到**調試**頁。 對於**命令**,鍵入[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE 的 路徑(預設情況下,這是 *[驅動器]*[程式檔]微軟[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]8_Common7_IDE_devenv.exe)。

3. 對於**命令參數**,`/rootsuffix exp`鍵入 實驗註冊表配置單元(在安裝 VSIP 時創建)。

4. 按一下 [確定] **** 以接受變更。

5. 通過按**F5**啟動項目類型。 這將啟動[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]的第二個實例。

6. 此時,您可以在項目類型原始程式碼中放置斷點。

7. 在的二個[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]實例中,載入或創建項目類型的新實例。 在載入或創建過程中,您的斷點可能會被擊中。

8. 調試項目類型。

9. 如果選擇調試啟動 DE 的過程,則可以執行「調試自定義調試引擎」過程中的步驟,以在啟動 DE 後附加到 DE。 這為您提供了三個[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]執行實例:一個用於項目類型源,第二個用於實例化項目類型,第三個實例附加到 DE。

## <a name="see-also"></a>另請參閱
- [建立自訂除錯引擎](../../extensibility/debugger/creating-a-custom-debug-engine.md)
