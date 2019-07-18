---
title: HOW TO：Debug an ActiveX Control |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vc.controls.debug
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- testing [Visual Studio], test containers
- ActiveX control container debugging [Visual Studio]
- debugging ActiveX controls
- data-bound controls, ActiveX
- test container
- containers, specifying for debug sessions
- ActiveX controls, debugging
- testing [Visual Studio], ActiveX controls
ms.assetid: bbc02cf7-a7e6-44fe-99af-87a43e1d7251
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9524ab08ab955609f29f437e8a1576af02738aa1
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65704456"
---
# <a name="how-to-debug-an-activex-control"></a>作法：對 ActiveX 控制項進行偵錯
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

注意]
> 根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [工具] 功能表中選擇 [匯入和匯出設定]。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
 若要偵錯您的 ActiveX 控制項，您必須指定容器 (可執行檔)，讓控制項在其中執行。  
  
### <a name="to-specify-a-container-for-the-debug-session"></a>若要指定此偵錯工作階段的容器  
  
1. 在 [方案總管] 中選取專案。  
  
2. 從**檢視**功能表上，選擇**屬性頁**。  
  
3. 在 [專案屬性頁] 對話方塊中，開啟 [組態屬性] 資料夾，並選取 [偵錯]。  
  
4. 在 [偵錯] 類別下方，找出 [命令] 屬性。  
  
5. 指定該容器的路徑名稱。 例如，C:\Program Files\Internet Explorer\IEXPLORE.EXE。  
  
6. 如果您指定 Internet Explorer 作為容器，而且您正使用 Active Desktop，請在 [命令引數] 方塊中鍵入 `/new`。  
  
7. 按一下 [確定] 。  
  
     若您未在 [專案屬性頁] 對話方塊中指定容器，您也可以在開始偵錯時指定容器。 當您選取執行命令以開始偵錯時，將會出現[偵錯工作階段的可執行檔對話方塊](../debugger/executable-for-debugging-session-dialog-box.md)。 在對話方塊中指定容器的路徑名稱。  
  
## <a name="see-also"></a>另請參閱  
 [ActiveX 控制項](https://msdn.microsoft.com/library/52aaec4d-3889-402e-b57d-758078f8ac57)   
 [使用測試容器測試屬性和事件](https://msdn.microsoft.com/library/626867cf-fe53-4c30-8973-55bb93ef3917)   
 [對 COM 和 ActiveX 進行偵錯](../debugger/com-and-activex-debugging.md)   
 [Visual Studio 偵錯](../debugger/debugging-in-visual-studio.md)
