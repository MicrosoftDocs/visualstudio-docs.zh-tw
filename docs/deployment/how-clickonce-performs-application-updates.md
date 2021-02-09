---
title: ClickOnce 如何執行應用程式更新 |Microsoft Docs
description: 瞭解 ClickOnce 如何使用檔案版本資訊來決定是否要更新應用程式。 ClickOnce 會使用檔案修補來避免下載多餘的檔案。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- updates, ClickOnce
- ClickOnce deployment, updates
- deploying applications [ClickOnce], application updates
ms.assetid: d54313c2-cf0c-420d-b151-99953a95f0bb
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: cdef39a0ab07d4cb9c9f42cf897bd7728934b88d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99915736"
---
# <a name="how-clickonce-performs-application-updates"></a>ClickOnce 執行應用程式更新的方式
ClickOnce 會使用應用程式部署資訊清單中指定的檔案版本資訊，來決定是否要更新應用程式的檔案。 開始更新之後，ClickOnce 會使用稱為「檔案 *修補* 」的技術，以避免重複下載應用程式檔。

## <a name="file-patching"></a>檔修補
 更新應用程式時，除非檔案已變更，否則 ClickOnce 不會下載新版本應用程式的所有檔案。 相反地，它會將目前應用程式之應用程式資訊清單中所指定檔案的雜湊簽章，與新版本資訊清單中的簽章進行比較。 如果檔案的簽章不同，ClickOnce 會下載新的版本。 如果簽章相符，檔案就不會從某個版本變更為下一個版本。 在此情況下，ClickOnce 會複製現有的檔案，並在新版本的應用程式中使用它。 這種方法可防止 ClickOnce 因為只有一或兩個檔案已變更，而不需要再次下載整個應用程式。

 檔案修補也適用于使用和方法視需要下載的元件 <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroup%2A> <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroupAsync%2A> 。

 如果您使用 Visual Studio 來編譯應用程式，它會在每次重建整個專案時，為所有檔案產生新的雜湊簽章。 在此情況下，雖然只有少陣列件可能已變更，但是所有的元件都會下載到用戶端。

 檔修補不適用於標示為數據並儲存在資料目錄中的檔案。 無論檔案的雜湊簽章為何，一律會下載這些檔案。 如需資料目錄的詳細資訊，請參閱 [在 ClickOnce 應用程式中存取本機和遠端資料](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md)。

## <a name="see-also"></a>另請參閱
- [選擇 ClickOnce 更新策略](../deployment/choosing-a-clickonce-update-strategy.md)
- [選擇 ClickOnce 部署策略](../deployment/choosing-a-clickonce-deployment-strategy.md)