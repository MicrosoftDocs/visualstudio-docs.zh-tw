---
title: 如何： 偵錯自訂偵錯引擎 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, debugging
- debugging [Debugging SDK], custom debug engines
ms.assetid: df27a8d6-3938-45ff-b47f-b684e80b38a0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 95a2db2bc5e8990f536abc851941c337a1dee277
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-debug-a-custom-debug-engine"></a>如何： 偵錯自訂偵錯引擎
專案類型會從啟動的偵錯引擎 (DE)<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A>方法。 這表示所控制的執行個體啟動時 DE[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]控制專案類型。 不過，該執行個體[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]無法偵錯 DE。 下面這樣是可讓您偵錯您的自訂 DE 的步驟。  
  
> [!NOTE]
>  ： 在 「 偵錯自訂偵錯引擎 」 程序中，您必須等待前，您可以附加至這個啟動 DE。 如果您即將 DE 啟動時，會出現您 DE 開始將訊息方塊，您可以附加在該點，然後清除 訊息方塊，以繼續。 這樣一來，您可以攔截所有 DE 事件。  
  
> [!WARNING]
>  您必須擁有才能嘗試進行下列程序安裝遠端偵錯。 請參閱[遠端偵錯](../../debugger/remote-debugging.md)如需詳細資訊。  
  
### <a name="debugging-a-custom-debug-engine"></a>偵錯自訂偵錯引擎  
  
1.  啟動 msvsmon.exe，遠端偵錯監視。  
  
2.  從**工具**功能表中選取 msvsmon.exe**選項**開啟**選項** 對話方塊。  
  
3.  選取 [沒有驗證] 選項，然後按一下**確定**。  
  
4.  啟動的執行個體[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]並開啟您的自訂 DE 專案。  
  
5.  開始的第二個執行個體[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]並開啟您的自訂專案，可啟動 DE （進行開發，這通常是在 VSIP 安裝時設定在實驗登錄區）。  
  
6.  這個第二個執行個體中[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]、 載入原始程式檔從您的自訂專案，並開始偵錯的程式。 請稍候片刻以允許載入，或等到中斷點叫用 DE。  
  
7.  第一個執行個體中[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]（DE 專案），然後選取 **附加至處理序**從**偵錯**功能表。  
  
8.  在**附加至處理序**對話方塊中，變更**傳輸**至**遠端 （僅限使用任何驗證的機器碼）**。  
  
9. 變更**限定詞**至您的電腦名稱 (請注意： 沒有記錄的項目，因此您必須輸入此名稱在一次)。  
  
10. 在**可用的處理序**清單中，選取執行個體正在執行，並按一下您 DE**附加** 按鈕。  
  
11. 符號載入您 DE 中之後，請在 DE 程式碼中放置中斷點。  
  
12. 每次您停止並重新啟動偵錯的程序，請重複步驟 6 到第 10。  
  
### <a name="debugging-a-custom-project-type"></a>偵錯自訂專案類型  
  
1.  啟動[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]在標準登錄區和負載專案輸入 （亦即，要您的專案類型，不具現化您的專案類型的來源） 的專案。  
  
2.  開啟專案屬性並移至**偵錯**頁面。 如**命令**，輸入路徑[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE (根據預設，這是 *[磁碟機]* \Program Files\Microsoft [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 8\Common7\IDE\devenv.exe)。  
  
3.  如**命令引數**，型別`/rootsuffix exp`的 （VSIP 安裝時建立） 在實驗登錄區。  
  
4.  按一下 [確定]  以接受變更。  
  
5.  按 f5 鍵啟動您的專案類型。 這樣就會啟動另一個執行個體[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
6.  此時，您可以在您的專案類型的原始程式碼中放置中斷點。  
  
7.  第二個執行個體中[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]、 載入或建立您的專案類型的新執行個體。 在載入或建立，您的中斷點可能會叫用。  
  
8.  偵錯您的專案類型。  
  
9. 如果您選擇偵錯啟動 DE 的程序，您可以執行 「 偵錯自訂偵錯引擎 」 程序啟動之後，將附加至您 DE 中的步驟。 這會提供三個執行個體[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]執行： 一個用於您的專案類型的來源，為您具現化的專案類型，以及協力廠商附加至您 DE 第二個。  
  
## <a name="see-also"></a>另請參閱  
 [建立自訂的偵錯引擎](../../extensibility/debugger/creating-a-custom-debug-engine.md)