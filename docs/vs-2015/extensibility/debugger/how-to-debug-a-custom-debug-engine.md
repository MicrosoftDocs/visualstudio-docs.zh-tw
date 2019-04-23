---
title: 如何：偵錯自訂的偵錯引擎 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, debugging
- debugging [Debugging SDK], custom debug engines
ms.assetid: df27a8d6-3938-45ff-b47f-b684e80b38a0
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7effa937a8faa0a238f8be2505ddf47223010bc1
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2019
ms.locfileid: "60039945"
---
# <a name="how-to-debug-a-custom-debug-engine"></a>如何：偵錯自訂的偵錯引擎
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

從專案類型會啟動的偵錯引擎 (DE)<xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A>方法。 這表示控制下的執行個體啟動時 DE[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]控制的專案類型。 不過，該執行個體[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]無法偵錯 DE。 下面是可讓您偵錯您的自訂裝置的步驟。  
  
> [!NOTE]
>  :   在 「 偵錯自訂偵錯引擎 」 程序中，您必須等待開始之前，您可以附加至這個 DE。 如果您即將開始您 DE DE 啟動時出現的訊息方塊，您可以附加在該點，然後清除 訊息方塊，以繼續。 如此一來，您可以攔截所有 DE 事件。  
  
> [!WARNING]
>  您必須擁有遠端偵錯安裝才能嘗試進行下列程序。 請參閱[遠端偵錯](../../debugger/remote-debugging.md)如需詳細資訊。  
  
### <a name="debugging-a-custom-debug-engine"></a>偵錯自訂的偵錯引擎  
  
1. 啟動 msvsmon.exe，遠端偵錯監視。  
  
2. 從**工具**功能表中選取 msvsmon.exe**選項**以開啟**選項** 對話方塊。  
  
3. 選取 [無驗證] 選項，然後按一下**確定**。  
  
4. 啟動的執行個體[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]並開啟您自訂的預設專案。  
  
5. 開始的第二個執行個體[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]並開啟您自訂的專案啟動 DE （對於程式開發，這通常是在實驗登錄區所設定，安裝 VSIP 時）。  
  
6. 在這個第二個執行個體[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]、 載入原始程式檔從您的自訂專案，並開始進行偵錯程式。 等候幾分鐘才能載入，或等候，直到遇到中斷點 DE。  
  
7. 第一個執行個體中[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]（DE 專案），然後選取 **附加至處理序**從**偵錯**功能表。  
  
8. 在 [ **připojit k procesu** ] 對話方塊中，變更**傳輸**來**遠端 （僅限使用任何驗證的原生）**。  
  
9. 變更**限定詞**您電腦的名稱 (注意： 沒有記錄的項目，因此您必須輸入此名稱一次)。  
  
10. 在 [**可用的處理序**清單中，選取執行個體正在執行，並按一下您 DE**附加**] 按鈕。  
  
11. 在您的裝置中載入符號之後，請您 DE 程式碼中放置中斷點。  
  
12. 每次您停止，並再重新啟動偵錯程序，請重複步驟 6 到 10。  
  
### <a name="debugging-a-custom-project-type"></a>偵錯自訂專案類型  
  
1. 啟動[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]在正常的登錄區和負載您的專案類型 （亦即，您的專案類型，不具現化您的專案類型的來源） 的專案。  
  
2. 開啟專案屬性，並移至**偵錯**頁面。 針對**命令**，輸入的路徑[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]IDE (根據預設，這是 *[磁碟機]* \Program Files\Microsoft [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 8\Common7\IDE\devenv.exe)。  
  
3. 針對**命令列引數**，型別`/rootsuffix exp`的實驗登錄區 （VSIP 安裝時建立）。  
  
4. 按一下 [確定]  以接受變更。  
  
5. 按 f5 鍵，以啟動您的專案類型。 這會啟動另一個執行個體[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]。  
  
6. 到目前為止，您也可以在您的專案類型的原始程式碼中放置中斷點。  
  
7. 第二個執行個體中[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]、 載入或建立您的專案類型的新執行個體。 在載入或建立時，您的中斷點可能會叫用。  
  
8. 偵錯您的專案類型。  
  
9. 如果您選擇偵錯啟動規定的處理序，您可以執行 「 偵錯自訂偵錯引擎 」 程序啟動之後附加至您的德國中的步驟。 這會提供三個執行個體[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]執行： 一個用於您的專案類型的來源，另一個則用於您具現化的專案類型，以及第三個附加至您的裝置。  
  
## <a name="see-also"></a>另請參閱  
 [建立自訂的偵錯引擎](../../extensibility/debugger/creating-a-custom-debug-engine.md)
