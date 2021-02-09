---
title: Windows Vista 的 ClickOnce 部署 |Microsoft Docs
description: 瞭解 Visual Studio 如何產生 ClickOnce 的外部 UAC 資訊清單，以及需要外部資訊清單 Registration-Free COM 應用程式。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- UAC manifest generation
- ClickOnce deployment, Windows
- manifest generation
- Windows, ClickOnce deployment
ms.assetid: b21a0ebc-0ff6-4f49-8993-7d1ad3f8cac2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ccac1cd234a0f83810ff2596e1763209d95a8325
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99918450"
---
# <a name="clickonce-deployment-on-windows-vista"></a>Windows Vista 的 ClickOnce 部署

在 Visual Studio 中建立應用程式以進行使用者帳戶控制 (UAC) 在 Windows Vista 上，通常會產生內嵌的資訊清單，並在應用程式的可執行檔中編碼為二進位 XML 資料。  ClickOnce 和 Registration-Free COM 應用程式需要外部資訊清單，因此 Visual Studio 會為這些專案產生檔案，其中包含 UAC 資料，而不是內嵌的資訊清單。 針對 ClickOnce 和 Registration-Free COM 部署，Visual Studio 會使用名為 *app.config* 的檔案中的資訊來產生外部 UAC 資訊清單資訊。 在所有其他情況下，Visual Studio 將 UAC 資料內嵌在應用程式的可執行檔中。

Visual Studio 針對資訊清單產生提供下列選項：

- 使用內嵌資訊清單。 將 UAC 資料內嵌在應用程式的可執行檔中，並以一般使用者的形式執行。

   除非您使用 ClickOnce) ，否則這是預設的 (設定。 這項設定支援在 Windows Vista 上進行 Visual Studio 操作的一般方式，同時也會使用產生內部和外部資訊清單 `AsInvoker` 。

- 使用外部資訊清單。 使用 *app.config* 產生外部資訊清單。

   這只會使用 *app.config* 中的資訊來產生外部資訊清單。 當您使用 ClickOnce 或 Registration-Free COM 發行應用程式時，Visual Studio 會將 *app.config* 新增至專案，然後加入此選項。

- 不使用資訊清單。 建立沒有資訊清單的應用程式。

   這種方法也稱為 *虛擬化*。 使用此選項可與舊版 Visual Studio 的現有應用程式相容。

  您可以在 [專案設計工具] 的 [ **應用程式** ] 頁面上找到新的屬性， (僅針對 Visual c # 專案) 和 MSBuild 專案檔案格式。

  在 Visual Studio IDE 中設定 UAC 資訊清單產生的方法，會因 Visual c # (或 Visual Basic) 的專案類型而有所不同。

  * 如需設定 Visual c # 專案以產生資訊清單的詳細資訊，請參閱 [應用程式頁面、專案設計工具 (c # ) ](../ide/reference/application-page-project-designer-csharp.md)。

  * 如需設定 Visual Basic 專案以產生資訊清單的詳細資訊，請參閱 [應用程式頁面、專案設計工具 (Visual Basic) ](../ide/reference/application-page-project-designer-visual-basic.md)。

## <a name="see-also"></a>另請參閱
- [ClickOnce 安全性和部署](../deployment/clickonce-security-and-deployment.md)
- [使用者權限和 Visual Studio](/previous-versions/ms165100(v=vs.100))
- [專案設計工具，應用程式頁 (C#)](../ide/reference/application-page-project-designer-csharp.md)
- [Application Page, Project Designer (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)