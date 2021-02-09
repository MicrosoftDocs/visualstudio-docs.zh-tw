---
title: 安全部署
description: 瞭解如何使用憑證來簽署解決方案，或使用 ClickOnce 信任提示索引鍵，以提供信任決策作為基礎的辨識項。
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- deploying applications [Office development in Visual Studio], security
- Office development in Visual Studio, security
- Office applications [Office development in Visual Studio], security
- ClickOnce deployment [Office development in Visual Studio], security
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: c778ed98a3f5d17007acccd2f16208ece3237037
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99906750"
---
# <a name="secure-deployment"></a>安全部署
  當您建立 Office 方案時，會自動更新您的開發電腦，以允許專案中的程式碼執行。 不過，當您部署方案時，您必須使用憑證來簽署解決方案，或使用信任提示金鑰，以提供信任決策作為基礎的辨識 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] 項。 如需詳細資訊，請參閱 [授與信任給 Office 方案](../vsto/granting-trust-to-office-solutions.md)。

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 針對檔層級自訂，如果您將檔部署到網路位置，您也必須將檔的位置加入 Office 應用程式信任中心內的信任位置清單。 如需有關如何在使用者電腦上設定檔許可權的詳細資訊，請參閱 [授與信任給檔](../vsto/granting-trust-to-documents.md)。

## <a name="prevent-office-solutions-from-running-code"></a>防止 Office 解決方案執行程式碼
 系統管理員可以使用登錄來防止所有 Office 方案在電腦上執行。 當開啟具有 managed 程式碼擴充功能的 Office 方案時，Visual Studio Tools for Office 執行時間會檢查 `Disabled` 電腦上下列其中一個登錄機碼下是否有名稱的專案：

- **HKEY_CURRENT_USER\Software\Microsoft\VSTO**

- **HKEY_LOCAL_MACHINE\Software\Microsoft\VSTO**

  若要防止 Office 方案執行程式碼，請 `Disabled` 在其中一個或兩個登錄機碼底下建立一個專案，並指定下列其中一種資料類型和值 `Disabled` ：

- REG_SZ 或 REG_EXPAND_SZ，其設定為 "0" (零) 以外的任何字串。

- 設定為 0 (零) 以外任何值的 REG_DWORD。

  若要讓 Office 方案可以執行程式碼，請將兩個 `Disabled` 專案設定為 0 (零) ，或刪除登錄專案。

## <a name="see-also"></a>另請參閱
- [部署 Office 方案](../vsto/deploying-an-office-solution.md)
- [準備要執行或裝載 Office 解決方案的電腦](/previous-versions/bb772092(v=vs.110))
- [保護 Office 方案](../vsto/securing-office-solutions.md)