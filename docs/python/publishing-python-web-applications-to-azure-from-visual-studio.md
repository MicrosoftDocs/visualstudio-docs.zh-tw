---
title: 將 Python 應用程式發佈到 Azure App Service
description: 適用於將 Python 應用程式發佈到 Azure App Service 的選項，包括 Git 部署及 Linux 的容器，以及部署到 IIS。
ms.date: 03/13/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: b2848a54ddbce41b538bf58f82db42ede76026d1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99912418"
---
# <a name="publish-to-azure-app-service"></a>發佈至 Azure App Service

目前在適用於 Linux 的 Azure App Service 上支援 Python，而且您可以使用 [Git 部署](#publish-to-app-service-on-linux-using-git-deploy)和[容器](#publish-to-app-service-on-linux-using-containers)發佈應用程式，如本文中所述。

> [!Note]
> 在適用於 Windows 的 Azure App Service 上，官方已淘汰 Python 支援。 因此，只有 [IIS 目標](#publish-to-iis)正式支援 Visual Studio 中的 [發佈] 命令，而且官方不再支援 Azure App Service 上的遠端偵錯。
>
> 不過，[發佈至 Windows 上的 App Service](publish-to-app-service-windows.md) 功能因為時間的關係仍能運作，因為在 Windows 上，App Service 的 Python 擴充功能仍然可用，但將不提供服務或更新。

## <a name="publish-to-app-service-on-linux-using-git-deploy"></a>使用 Git 部署發佈至 Linux 上的 App Service

Git 部署可將 Linux 上的 App Service 連線至特定的 Git 存放庫分支。 將程式碼自動提交到該分支可部署至 App Service，而且 App Service 會自動安裝 *requirements.txt* 中所列的任何相依性。 在此情況下，Linux 上的 App Service 會在預先設定的容器映像中，執行使用 Gunicorn 網頁伺服器的程式碼。 此服務目前為預覽狀態，並不支援用於生產環境。

如需詳細資訊，請參閱 Azure 文件中的下列文章：

- [快速入門：在 App Service 中建立 Python Web 應用程式](/azure/app-service/containers/quickstart-python?toc=%2Fpython%2Fazure%2FTOC.json)提供簡短的逐步解說，說明如何使用本機 Git 存放庫中的簡單 Flask 應用程式和部署，進行 Git 部署程序。
- [如何設定 Python](/azure/app-service/containers/how-to-configure-python)說明 Linux 容器上的 App Service 特性，以及如何自訂您應用程式的 Gunicorn 啟動命令。

## <a name="publish-to-app-service-on-linux-using-containers"></a>使用容器發佈至 Linux 上的 App Service

您可以提供自己的容器，而不依賴使用 Linux 上的 App Service 預先建置的容器。 此選項可讓您選擇所使用的網頁伺服器，並自訂容器的行為。

有兩個選項可以用來建置、管理及推送容器：

- 使用 Visual Studio Code 和 Docker 擴充功能，如[使用 Docker 容器部署 Python](https://code.visualstudio.com/docs/python/tutorial-deploy-containers) 上所述。 即使您未使用 Visual Studio Code，本文還是會針對使用實際執行的 uwsgi 和 nginx 網頁伺服器的 Flask 和 Django 應用程式，提供有關建置容器映像的實用詳細資料。 接著，您可以使用 Azure CLI，部署這些相同的容器。

- 使用命令列與 Azure CLI，如 Azure 文件中的[使用自訂的 Docker 映像](/azure/app-service/containers/tutorial-custom-docker-image)所述。 但是這是一般指南，並不限於 Python。

## <a name="publish-to-iis"></a>發佈至 IIS

您可以使用 [發佈] 命令，從 Visual Studio 發佈至 Windows 虛擬機器或其他支援 IIS 的電腦。 使用 IIS 時，請務必在應用程式中建立或修改 *web.config* 檔案，告訴 IIS 在哪裡可以找到 Python 解譯器。 如需詳細資訊，請參閱[為 Web 應用程式設定 IIS](configure-web-apps-for-iis-windows.md)。
