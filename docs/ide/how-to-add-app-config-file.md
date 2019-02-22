---
title: 如何將 app.config 檔案新增至專案
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
helpviewer_keywords:
- app.config files, adding to C# projects
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: d7e760d952d03a31fdb633ae57c0fb670b50fcc2
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2019
ms.locfileid: "55937291"
---
# <a name="how-to-add-an-application-configuration-file-to-a-c-project"></a>HOW TO：將應用程式組態檔新增至 C# 專案

您可以將應用程式組態檔 (app.config 檔案) 新增至 C# 專案，以自訂通用語言執行平台尋找及載入組件檔的方式。 如需應用程式組態檔的詳細資訊，請參閱[執行階段如何找出組件 (.NET Framework)](/dotnet/framework/deployment/how-the-runtime-locates-assemblies)。

> [!NOTE]
> UWP 應用程式不包含 app.config 檔案。

當您建置專案時，開發環境會自動複製您的 app.config 檔案，並將複本的檔案名稱變更為符合可執行檔的名稱，然後移動到 **bin** 目錄。

## <a name="to-add-an-application-configuration-file-to-a-c-project"></a>將應用程式組態檔加入 C# 專案

1. 在功能表列中，選擇 [專案] > [加入新項目]。

     [新增項目] 對話方塊隨即出現。

1. 展開 [已安裝] > [Visual C# 項目]，然後選擇 [應用程式組態檔] 範本。

1. 在 [名稱] 文字方塊中，輸入名稱，然後選擇 [新增] 按鈕。

     名為 *app.config* 的檔案會新增至專案。

## <a name="see-also"></a>另請參閱

- [管理應用程式設定 (.NET)](../ide/managing-application-settings-dotnet.md)
- [組態檔結構描述 (.NET Framework)](/dotnet/framework/configure-apps/file-schema/index)
- [設定應用程式 (.NET Framework)](/dotnet/framework/configure-apps/index)