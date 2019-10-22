---
title: 如何：將應用程式佈建檔新增至C#專案 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
dev_langs:
- CSharp
helpviewer_keywords:
- app.config files, adding to C# projects
ms.assetid: 9caf6bb0-c2fc-4ab6-ba69-bed3b880fbf8
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f8417b5520dc9587fa3231a3bc459335d2a9896d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667524"
---
# <a name="how-to-add-an-application-configuration-file-to-a-c-project"></a>如何：將應用程式組態檔加入至 C# 專案
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

您可以將應用程式組態檔 (app.config 檔案) 加入 C# 專案，以自訂通用語言執行平台尋找及載入組件檔的方式。 如需應用程式佈建檔的詳細資訊，請參閱[執行時間如何找出元件](https://msdn.microsoft.com/library/772ac6f4-64d2-4cfb-92fd-58096dcd6c34)。

> [!NOTE]
> Windows Store 不支援 <xref:System.Configuration>。 因此，存放區應用程式不包含 app.config 範本。

 當您建立專案時，開發環境會自動複製您的 app.config 檔案，將複本的檔案名變更為符合可執行檔，然後將複本移至 bin 目錄。

### <a name="to-add-an-application-configuration-file-to-your-c-project"></a>將應用程式佈建檔新增至您C#的專案

1. 在功能表列上，選擇 [**專案**]、[**加入新專案**]。

     [新增項目] 對話方塊隨即出現。

2. 展開 [**已安裝**]，展開 [**視覺C#專案**]，然後選擇 [**應用程式佈建檔**] 範本。

3. 在 [名稱] 文字方塊中，輸入名稱，然後選擇 [新增] 按鈕。

     名為 app.config 的檔案會新增至您的專案。

## <a name="see-also"></a>請參閱
 [管理應用程式設定（.net）](../ide/managing-application-settings-dotnet.md) [設定檔架構](https://msdn.microsoft.com/library/69003d39-dc8a-460c-a6be-e6d93e690b38)設定[應用](https://msdn.microsoft.com/library/86bd26d3-737e-4484-9782-19b17f34cd1f)程式[如何：設定應用程式以](https://msdn.microsoft.com/5247b307-89ca-417b-8dd0-e8f9bd2f4717)[使用 Visual Studio 開發環境C# ](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md)的 .NET Framework 版本為目標