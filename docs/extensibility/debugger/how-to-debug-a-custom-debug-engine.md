---
title: 如何：將自訂的 Debug Engine 進行調試 |Microsoft Docs
description: 瞭解可讓您使用 Visual Studio 來將自訂的 debug engine 或自訂專案類型進行偵錯工具的步驟。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debug engines, debugging
- debugging [Debugging SDK], custom debug engines
ms.assetid: df27a8d6-3938-45ff-b47f-b684e80b38a0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 46e9b18f7bb34433ff86fe6a5bede436228d3ff1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99947693"
---
# <a name="how-to-debug-a-custom-debug-engine"></a>如何：將自訂的 debug engine 進行調試
專案類型會啟動 debug engine (從方法中取消) <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> 。 這表示會在控制專案類型的實例控制下啟動取消 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。 但是，該實例 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 無法解除對 DE 的偵錯工具。 接下來的步驟可讓您進行自訂的 DE 錯。

> [!NOTE]
> ：在「自訂偵錯工具引擎」程式中，您必須先等候「取消」開始，然後才能附加至該程式。 如果您將訊息方塊放在取消開始時出現的地方，您可以在該點附加，然後清除訊息方塊以繼續。 如此一來，您就可以攔截所有的取消事件。

> [!WARNING]
> 您必須先安裝遠端偵錯程式，然後再嘗試執行下列程式。 如需詳細資料，請參閱 [遠端偵錯](../../debugger/remote-debugging.md) 程式。

## <a name="debug-a-custom-debug-engine"></a>自訂調試引擎

1. 啟動 *msvsmon.exe*，遠端偵錯監視器。

2. 從 *msvsmon.exe* 的 [**工具**] 功能表中選取 [**選項**]，以開啟 [**選項**] 對話方塊。

3. 選取 [無驗證] 選項，然後按一下 **[確定]**。

4. 啟動的實例 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ，並開啟您的自訂 DE 專案。

5. 啟動的第二個實例， [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 然後開啟您的自訂專案，此專案會啟動要進行開發的 DE (，這通常是在安裝 VSIP 時所設定的實驗登錄 hive) 。

6. 在的第二個實例中 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ，從您的自訂專案載入原始程式檔，然後啟動要進行調試的程式。 等候幾分鐘的時間，以允許取消載入，或等候直到點擊中斷點為止。

7. 在 (的第一個實例中 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ，當您取消專案) ，請從 [**調試** 程式] 功能表中選取 [**附加至進程**]。

8. 在 [ **附加至進程** ] 對話方塊中，將 [ **傳輸** ] 變更 (為 [ **僅限原生，而不使用驗證)**]。

9. 將辨識 **符號** 變更為您的電腦名稱稱 (注意：有專案的歷程記錄，因此您只需要在) 時輸入此名稱一次。

10. 在 [ **可使用的進程** ] 清單中，選取正在執行的 DE 實例，然後按一下 [ **附加** ] 按鈕。

11. 將符號載入您的 DE 之後，將中斷點放在您的 DE 程式碼中。

12. 每次停止然後重新開機偵錯工具時，請重複步驟6到10。

## <a name="debug-a-custom-project-type"></a>Debug 自訂專案類型

1. 從 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 一般登錄區開始，然後載入您的專案類型專案 (這是您專案類型的來源，而不是專案類型的具現化) 。

2. 開啟專案屬性，並移至 [ **Debug** ] 頁面。 在 **命令** 中，輸入 IDE (的路徑 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ，預設為 *[磁片磁碟機]* \Program Files\Microsoft [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 8\Common7\IDE\devenv.exe) 。

3. 在 [ **命令引數**] 中，輸入 `/rootsuffix exp` (在安裝 VSIP 時所建立的實驗登錄 hive) 。

4. 按一下 [確定]  以接受變更。

5. 按下 **F5** 以啟動您的專案類型。 這會啟動的第二個實例 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。

6. 此時，您可以將中斷點放置在您的專案類型原始程式碼中。

7. 在的第二個實例中 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ，載入或建立專案類型的新實例。 在載入或建立期間，您可能會遇到中斷點。

8. 進行專案類型的偵錯工具。

9. 如果您選擇要對啟動取消的程式進行偵錯工具，您可以執行「將自訂的偵錯工具引擎進行偵錯工具」程式中的步驟，以在啟動後附加至您的 DE。 這會提供您三個 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 執行的實例：一個適用于您的專案類型來源、第二個用於具現化的專案類型，第三個則附加至您的 DE。

## <a name="see-also"></a>另請參閱
- [建立自訂的調試引擎](../../extensibility/debugger/creating-a-custom-debug-engine.md)
