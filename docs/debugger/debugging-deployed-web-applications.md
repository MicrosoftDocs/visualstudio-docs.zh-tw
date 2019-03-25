---
title: 偵錯已部署的 ASP.NET 應用程式 |Microsoft Docs
ms.date: 06/30/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- ASP.NET Web applications
- Web services, debugging
- XML, debugging Web services
- debugging Web services
- ASP.NET, debugging Web applications
- XML Web services, debugging
ms.assetid: b938a91b-be96-416f-83bc-4177e7f3929a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: 57594775afe5d6708cd5d11b141f8cffc1b42e6c
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: MTE95
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57525384"
---
# <a name="debugging-deployed-aspnet-applications"></a>偵錯已部署的 ASP.NET 應用程式
若要使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 偵錯已部署的應用程式，您必須附加至 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 背景工作處理序，並且確定偵錯工具可以存取應用程式的符號。 您還必須找出並開啟應用程式的原始程式檔 (Source File)。 如需詳細資訊，請參閱 <<c0> [ 指定符號 (.pdb) 和原始程式檔](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)，[如何： 尋找 ASP.NET 處理序名稱](../debugger/how-to-find-the-name-of-the-aspnet-process.md)，並[系統需求](../debugger/aspnet-debugging-system-requirements.md)。

> [!WARNING]
> 如果您附加到[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]背景工作處理序進行偵錯及叫用中斷點時，所有受管理的背景工作處理序會中止的程式碼。 中止背景工作處理序中所有 Managed 程式碼可能會使伺服器上所有使用者的作業停止。 在實際執行伺服器上偵錯之前，請務必考慮對實際執行工作的可能影響。

用來附加至 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] 背景工作處理序的處理序，和附加至其他任何遠端處理序一樣。 當您附加之後，如果您未開啟正確的專案，則在應用程式中斷時會出現對話方塊。 這個對話方塊會要求您輸入應用程式原始程式檔的位置。 您在對話方塊中所指定的檔名，必須符合偵錯符號 (位於 Web 伺服器上) 中指定的檔名。 如需詳細資訊，請參閱 <<c0> [ 附加至執行的處理序](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)。 若要設定在 IIS 上的遠端偵錯，請參閱[Remote Debugging ASP.NET on a Remote IIS Computer](../debugger/remote-debugging-aspnet-on-a-remote-iis-computer.md)。

> [!NOTE]
>  許多 [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web 應用程式都會參考到包含商務邏輯或其他實用程式碼的 DLL。 這類的參考將從本機電腦，到 Web 應用程式的虛擬目錄的 \bin 資料夾複製 DLL，當您部署您的應用程式時也一樣。 在偵錯時請記住，您的 Web 應用程式是參考該 DLL 的複本而非本機電腦上的複本。

## <a name="see-also"></a>請參閱
- [針對 ASP.NET 應用程式進行偵錯](../debugger/how-to-enable-debugging-for-aspnet-applications.md)
- [如何：啟用 ASP.NET 應用程式的偵錯](../debugger/how-to-enable-debugging-for-aspnet-applications.md)
- [如何：尋找 ASP.NET 處理序的名稱](../debugger/how-to-find-the-name-of-the-aspnet-process.md)
- [指定符號 (.pdb) 和來源檔案](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)