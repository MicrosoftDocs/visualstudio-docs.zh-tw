---
title: 分析和 Windows Vista 安全性 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools,security
- performance tools, security
ms.assetid: 842112fc-b886-4801-8cd7-a25b314b0393
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d7e485bc6289634e1bb6d4b4106d54c8dc82096b
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65683693"
---
# <a name="profiling-and-windows-vista-security"></a>分析和 Windows Vista 安全性
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

依據電腦系統管理員提供的 [!INCLUDE[wiprlhext](../includes/wiprlhext-md.md)] 使用者存取權限設定，個別使用者可能具有安全性權限可以在該電腦上分析處理序。 下列範例説明各使用者之間可能存在的差異：  
  
- 當系統管理員設定了要啟動的驅動程式和服務時，某些使用者可以存取進階的程式碼剖析功能。  
  
- 網域使用者只能存取取樣程式碼剖析。  
  
- 某些使用者可以拒絕其他所有使用者存取程式碼剖析。  
  
  如需詳細資訊，請參閱 [VSPerfCmd](../profiling/vsperfcmd.md) 中的 ADMIN 選項。  
  
## <a name="cross-session-profiling"></a>跨工作階段進行程式碼剖析  
 「跨工作階段進行程式碼剖析」是指能夠分析在不同登入工作階段中執行的處理序。 例如，大部分服務是在工作階段 0 中執行，而使用者無法直接在工作階段 0 中執行。 使用 [效能總管] 工具列上的 [附加至處理序] 按鈕或 VSPerfCmd 命令列工具的 /attach 選項，您就可以分析不同登入工作階段中的大部分處理序。  
  
 您透過設定跨處理序進行程式碼剖析可見性選項，就可以看到處理序清單。 當您按一下 [附加至處理序] 後，隨即顯示的 [附加至處理序] 視窗中，會提供這些選項：  
  
- **顯示所有使用者的處理序**  
  
     未選取此選項時，清單只會顯示目前使用者所擁有的處理序。 選取 [顯示所有使用者的處理序] 時，清單才會顯示所有使用者的處理序。  
  
- **顯示所有工作階段中的處理序**  
  
     未選取此選項時，清單會顯示目前工作階段中的處理序。 選取此選項時，清單才會顯示所有工作階段中的處理序。  
  
## <a name="see-also"></a>另請參閱  
 [概觀](../profiling/overviews-performance-tools.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [如何：附加至執行中處理序](https://msdn.microsoft.com/636d0a52-4bfd-48d2-89ad-d7b9ca4dc4f4)
