---
title: "將 SCVMM 2008 R2 升級至 SCVMM 2012 | Microsoft Docs"
ms.custom: 
ms.date: 05/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Upgrade SCVMM 2008 R2 to SCVMM 2012, test lab
ms.author: gewarren
manager: ghogen
ms.workload: multiple
author: gewarren
ms.openlocfilehash: 51d907dfe25d8f27065b2a4d8bbecaa3e98e42a1
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2018
---
# <a name="upgrade-scvmm-2008-r2-to-scvmm-2012"></a>將 SCVMM 2008 R2 升級至 SCVMM 2012

Lab Management for Team Foundation Server 支援 SCVMM 2008 R2 和 SCVMM 2012。 如果您要將 Team Foundation Server 2013 升級至 Team Foundation Server 2015，並計劃將 SCVMM 2008 R2 升級至 SCVMM 2012，建議您先完成升級至 Team Foundation Server 2015 之後，再升級至 SCVMM 2012。 本主題說明如何在 Team Foundation Server 2015 上使用 Lab Management 時，從 SCVMM 2008 R2 升級至 SCVMM 2012。
Lab Management **不**支援 SCVMM 2016。 

**重要：**當您升級 SCVMM 時，某些步驟可能會造成您的 Team Foundation Server 停機。 您會在下文發現這些步驟。

## <a name="upgrading-to-scvmm-2012"></a>升級至 SCVMM 2012

1. 使用 SCVMM 2012 安裝程式將 SCVMM 2008 R2 Server 升級至 SCVMM 2012 Server。

1. 在您的主機和程式庫共用上升級 SCVMM 代理程式。

1. 使用 SCVMM 管理主控台驗證所有的 SCVMM 元件皆可運作。

1. 在 Team Foundation Server 應用程式層的所有電腦上安裝 SCVMM 2012 管理主控台。

1. 使用 **iisreset** 命令重新啟動 Team Foundation Server Web 服務。 然後重新啟動 Team Foundation Server 工作代理程式。

   **注意：**這個步驟會中斷 Team Foundation Server 的服務。

1. 請升級每個專案集合資料庫中的資料和範本，使其與 SCVMM 相容。 
   2012.

   在 Team Foundation Server 上開啟提升權限的命令提示字元，並輸入下列命令：

   **C:\\Program Files\\Microsoft Team Foundation Server 14.0\\Tools\> tfsconfig lab /upgradeSCVMM /collectionName:\***

   當您使用 **upgradeSCVMM** 命令時，Team Foundation Server 會在 SCVMM 伺服器上針對使用該範本的所有 Team 專案，建立新範本物件。 這可確保您的範本升級後將與 SCVMM 2012 相容且不會遺失任何資料。 不過，在建立新的範本時，Team 專案名稱會附加至範本名稱。

   **注意：**  
   如果新範本名稱的長度超過 64 個字元，則會導致 SCVMM 失敗。 若要解決這個錯誤，您必須以較短的名稱為這些範本命名。 如果在執行命令時發生任何其他錯誤或警告，請參閱下一節來解決這些錯誤。 如果未發生任何錯誤或警告，則升級作業完成後，您可以透過 Lab Management 開始使用 SCVMM 環境。

## <a name="resolving-errors-and-warnings-when-using-the-upgradescvmm-command"></a>解決使用 upgradeSCVMM 命令時所發生的錯誤和警告

在您使用 **upgradeSCVMM** 命令之後，您必須先解決收到的任何錯誤或警告再重新執行命令，才能開始使用 Lab Management。 **upgradeSCVMM** 命令會產生包含所有錯誤訊息和警告的記錄檔。 當您執行 **upgradeSCVMM** 命令時，記錄檔的位置會顯示出來。

**SCVMM 失敗：**如果收到與 SCVMM 失敗有關的錯誤，請使用您的 SCVMM 工作記錄取得與錯誤有關的其他資訊。 解決 SCVMM 中的錯誤之後，傳回 **upgradeSCVMM** 命令。

## <a name="see-also"></a>另請參閱

* [變更現有 Lab Management 組態](https://msdn.microsoft.com/library/ee704508%28v=vs.140%29.aspx)
