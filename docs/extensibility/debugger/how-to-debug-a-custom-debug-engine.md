---
title: 如何： Debug 自訂的 Debug Engine |Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- debug engines, debugging
- debugging [Debugging SDK], custom debug engines
ms.assetid: df27a8d6-3938-45ff-b47f-b684e80b38a0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a65e69655c4e8699bd267f1835ec0c49603014d7
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2020
ms.locfileid: "85903311"
---
# <a name="how-to-debug-a-custom-debug-engine"></a>如何： Debug 自訂的 debug engine
專案類型會從方法啟動 debug engine （DE） <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> 。 這表示會在控制專案類型之實例的控制項底下，啟動 DE [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。 不過，該實例 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 無法對 DE 進行 debug。 接下來的步驟可讓您進行自訂 DE 的偵錯工具。

> [!NOTE]
> ：在「偵錯工具自訂的偵錯工具引擎」程式中，您必須等候取消啟動，才能附加至該程式。 如果您將訊息方塊放在開始執行時出現在 de 的開頭附近，您可以在該時間點附加，然後清除訊息方塊以繼續。 如此一來，您就可以攔截所有的 DE 事件。

> [!WARNING]
> 您必須先安裝遠端偵錯程式，然後再嘗試執行下列程式。 如需詳細資訊，請參閱[遠端偵錯](../../debugger/remote-debugging.md)程式。

## <a name="debug-a-custom-debug-engine"></a>Debug 自訂的 debug engine

1. 啟動*msvsmon.exe*，即遠端 Debug 監視。

2. 從*msvsmon.exe*的 [**工具**] 功能表中，選取 [**選項**] 以開啟 [**選項**] 對話方塊。

3. 選取 [沒有驗證] 選項，然後按一下 **[確定]**。

4. 啟動的實例 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ，並開啟您的自訂取消專案。

5. 啟動的第二個實例 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ，並開啟啟動 DE 的自訂專案（用於開發，這通常是在安裝 VSIP 時設定的實驗登錄 hive 中）。

6. 在的第二個實例中 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ，從您的自訂專案載入原始程式檔，並啟動要進行偵錯工具。 等候幾分鐘的時間，允許取消載入，或等到到達中斷點為止。

7. 在的第一個實例 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] （使用您的 DE 專案）中，從 [**調試**程式] 功能表選取 [**附加至進程**]。

8. 在 [**附加至進程**] 對話方塊中，將 [**傳輸**] 變更為 [**遠端（僅限原生但不驗證）**]。

9. 將辨識**符號**變更為您的電腦名稱稱（注意：有專案的歷程記錄，因此您只需要輸入此名稱一次）。

10. 在 [**可使用的進程**] 清單中，選取正在執行之 DE 的實例，然後按一下 [**附加**] 按鈕。

11. 在您的 DE 中載入符號之後，請將中斷點放在您的 DE 程式碼中。

12. 每次您停止再重新開機偵錯工具時，請重複步驟6到10。

## <a name="debug-a-custom-project-type"></a>Debug 自訂專案類型

1. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]在一般登錄區中啟動，並載入您的專案類型專案（這是您的專案類型的來源，而不是專案類型的具現化）。

2. 開啟專案屬性，並移至 [ **Debug** ] 頁面。 針對**命令**，輸入 IDE 的路徑 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] （根據預設，這是 *[drive]* \Program Files\Microsoft [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 8\Common7\IDE\devenv.exe）。

3. 針對 [**命令引數**]，針對實驗性登錄 `/rootsuffix exp` hive （在安裝 VSIP 時建立）輸入。

4. 按一下 [確定] **** 以接受變更。

5. 按**F5**啟動您的專案類型。 這會啟動的第二個實例 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。

6. 此時，您可以將中斷點放在專案類型的原始程式碼中。

7. 在的第二個實例中 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ，載入或建立專案類型的新實例。 在載入或建立期間，可能會遇到中斷點。

8. Debug 您的專案類型。

9. 如果您選擇要對啟動 DE 的程式進行偵錯工具，您可以執行「自訂的偵錯工具引擎」程式中的步驟，以在啟動之後附加至您的 DE。 這會提供您三個 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 執行的實例：一個用於您的專案類型來源，第二個用於具現化的專案類型，而第三個則附加至您的 DE。

## <a name="see-also"></a>另請參閱
- [建立自訂的 debug engine](../../extensibility/debugger/creating-a-custom-debug-engine.md)
