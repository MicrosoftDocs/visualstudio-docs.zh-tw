---
title: 分析和 Windows Vista 安全性 | Microsoft Docs
description: 根據可用的使用者存取權限設定，個別使用者可能具有安全性許可權來分析該電腦上的處理常式。
ms.date: 11/02/2018
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools,security
- performance tools, security
ms.assetid: 842112fc-b886-4801-8cd7-a25b314b0393
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 0419ae09f2b43b396062fc8a3232b0a63c81483c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99936388"
---
# <a name="profiling-and-windows-vista-security"></a>分析和 Windows Vista 安全性

依據電腦系統管理員提供的 [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)] 使用者存取權限設定，個別使用者可能具有安全性權限可以在該電腦上分析處理序。 下列範例説明各使用者之間可能存在的差異：

- 當系統管理員設定了要啟動的驅動程式和服務時，某些使用者可以存取進階的程式碼剖析功能。

- 網域使用者只能存取取樣程式碼剖析。

- 某些使用者可以拒絕其他所有使用者存取程式碼剖析。

  如需詳細資訊，請參閱 [VSPerfCmd](../profiling/vsperfcmd.md) 中的 ADMIN 選項。

## <a name="cross-session-profiling"></a>跨工作階段進行程式碼剖析

「跨工作階段進行程式碼剖析」是指能夠分析在不同登入工作階段中執行的處理序。 例如，大部分服務是在工作階段 0 中執行，而使用者無法直接在工作階段 0 中執行。 使用 [效能總管] 工具列上的 [附加至處理序] 按鈕或 VSPerfCmd 命令列工具的 `/attach` 選項，您就可以分析不同使用者工作階段中的大部分處理序。

您透過設定跨處理序進行程式碼剖析可見性選項，就可以看到處理序清單。 當您選取 [附加至處理序] 後，隨即顯示的 [附加至處理序] 視窗中會提供這些選項：

- **顯示所有使用者的處理序**

  未選取此選項時，清單只會顯示目前使用者所擁有的處理序。 否則，清單會顯示所有使用者的處理序。

- **顯示所有工作階段中的處理序**

  未選取此選項時，清單會顯示目前工作階段中的處理序。 否則，清單會顯示所有工作階段中的處理序。

## <a name="see-also"></a>另請參閱

- [概觀](../profiling/overviews-performance-tools.md)
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [ 如何：附加至執行中的處理序](/previous-versions/visualstudio/visual-studio-2010/c6wf8e4z\(v\=vs.100\))
