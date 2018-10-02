---
title: 建立資料應用程式 |Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data access [Visual Studio], creating applications
- applications [Visual Studio], data
- data [Visual Studio]
- data [Visual Studio], creating applications
ms.assetid: ab334d5f-4f49-4346-bce0-3325d6130b3e
caps.latest.revision: 41
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 9e662eedef9053a460ffbb5012a079f05239a9a1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "47490502"
---
# <a name="creating-data-applications"></a>建立資料應用程式
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 提供許多設計階段工具，可協助您建立存取資料的應用程式。 本簡介提供有關建立搭配資料使用之應用程式的基本程序概觀。 這裡的資訊刻意略過許多細節，並設計做為與建立資料應用程式相關的許多其他 [說明] 頁的一般資訊來源和起點。  
  
 當您在 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 中開發存取資料的應用程式時，會有不同需求。 在一些情況下，您可能只要將資料顯示在表單上。 而在另一些情況下，您可能需要設計一個方法，與其他應用程式或處理序共用資訊。  
  
 不論您如何處理資料，都應該了解特定基礎概念。 您可能永遠都不需要知道資料處理的某些細節 (例如，以程式設計方式建立資料庫)，但是了解基本資料概念以及 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 的資料工具 (精靈和設計工具)，非常有用。  
  
 一般資料應用程式會使用下圖中說明的大部分程序：  
  
 ![資料循環圖形](../data-tools/media/datacyclegraphicinfo.gif "datacyclegraphicinfo")  
資料循環  
  
 當您建立應用程式時，思考要完成的工作。 請利用下列幾節的資訊，協助您尋找合適的 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 工具和物件。  
  
> [!NOTE]
>  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 可提供精靈以簡化上圖所顯示的數個流程。 例如，執行**資料來源組態精靈**提供您足夠的資訊來連接到資料、 建立具類型的資料集，以接收資料，並將資料帶入您的應用程式的應用程式。  
  
 若要快速查看如何[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]協助您開發資料應用程式，請參閱 <<c2> [ 逐步解說： 建立簡單的資料應用程式](http://msdn.microsoft.com/library/c5d0968c-d86f-4ae9-a2e1-871f208a3bb3)。  
  
## <a name="connecting-to-data"></a>連接到資料  
 若要將資料送回應用程式中 (並將變更傳送回資料來源)，必須建立特定雙向通訊類型。 這個雙向通訊一般是由資料模型中的物件所處理。  
  
 例如，`TableAdapter` 會將使用資料集的應用程式連接至資料庫，而 <xref:System.Data.Objects.ObjectContext> 則會將 Entity Framework 中的實體連接至資料庫。 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 提供幾種工具，可協助建立您的應用程式可以使用的連線。 如需有關您應用程式連接至資料的詳細資訊，請參閱[連接到 Visual Studio 中的資料](../data-tools/connecting-to-data-in-visual-studio.md)。  
  
 若要了解如何使用資料集，應用程式連接到資料庫中的資料，請參閱[逐步解說： 連接到資料庫 (Windows Form) 中的資料](http://msdn.microsoft.com/library/02d39aa6-8993-4602-be13-a13536af3d1c)。  
  
## <a name="preparing-your-application-to-receive-data"></a>準備您的應用程式以接收資料  
 如果您的應用程式使用中斷連接的資料模型，則當您使用此資料模型時，必須暫時將資料儲存在應用程式中。 Visual Studio 提供的工具可幫助您建立物件，讓應用程式用於暫存資料：資料集、實體和 [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] 物件。  
  
> [!NOTE]
>  使用中斷連接之資料模型的應用程式，通常會連接至資料庫、執行查詢將資料送回應用程式中、中斷與資料庫的連接，然後以離線方式管理資料，再重新連接和更新資料庫。  
  
 如需有關如何在您的應用程式中建立具類型資料集的詳細資訊，請參閱[準備您的應用程式接收資料](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)。 如需使用多層式架構應用程式中的資料集的詳細資訊，請參閱[分成不同的專案中的資料集和 Tableadapter](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)。  
  
 若要了解如何建立資料集，請完成中的程序[逐步解說： 以 Dataset 設計工具建立資料集](../data-tools/walkthrough-creating-a-dataset-with-the-dataset-designer.md)。  
  
 若要了解如何建立[!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)]物件，請完成中的程序[逐步解說： 建立的 LINQ to SQL 類別 （O-R 設計工具）](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)。  
  
## <a name="fetching-data-into-your-application"></a>將資料擷取至您的應用程式中  
 不論應用程式是否使用中斷連接資料模型，都必須能夠擷取資料放入應用程式中。 透過對資料庫執行查詢或預存程序，將資料送回應用程式中。 藉由使用儲存在資料集中的應用程式執行查詢和預存程序`TableAdapter`s，而將資料儲存在實體的應用程式使用執行查詢[LINQ to Entities](http://msdn.microsoft.com/library/641f9b68-9046-47a1-abb0-1c8eaeda0e2d)或藉由連接的實體直接到預存程序。 如需有關建立和編輯使用 Tableadapter 查詢的詳細資訊，請參閱 <<c0> [ 如何： 建立 TableAdapter 查詢](../data-tools/how-to-create-tableadapter-queries.md)並[如何： 編輯 TableAdapter 查詢](../data-tools/how-to-edit-tableadapter-queries.md)。  
  
 如需有關資料集，將資料載入和執行查詢和預存程序的詳細資訊，請參閱[將資料提取到您的應用程式](../data-tools/fetching-data-into-your-application.md)。  
  
 若要了解如何將資料載入資料集，請完成中的程序[逐步解說： 顯示 Windows Form 上的資料](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)檢查表單載入事件處理常式中的程式碼。  
  
 若要了解如何將資料載入[!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)]物件，請完成中的程序[逐步解說： 建立的 LINQ to SQL 類別 （O-R 設計工具）](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)。  
  
 若要了解如何建立和執行 SQL 查詢，請參閱[如何： 建立和執行 SQL 陳述式的傳回資料列](http://msdn.microsoft.com/library/14637fc5-d42a-4cca-97ac-54c181ec3eed)。  
  
 若要了解如何執行預存程序，請參閱[如何： 執行預存程序的傳回資料列](http://msdn.microsoft.com/library/db3d7021-d3ef-4db8-b12a-b6146570355d)。  
  
## <a name="displaying-data-on-forms"></a>在表單中顯示資料  
 將資料送至應用程式後，通常會在表單上顯示資料，供使用者檢視或修改。 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 提供[資料來源視窗](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)，您可以在其中拖曳至表單，自動建立顯示資料的資料繫結控制項的項目。 如需有關資料繫結和資料顯示給使用者的詳細資訊，請參閱[控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)。  
  
 若要了解如何將資料呈現給使用者，請完成下列逐步解說中的程序 (特別注意的項目從程序**Zdroje dat**視窗):  
  
-   [逐步解說： 顯示 Windows Form 上的資料](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)。  
  
-   [將 WPF 控制項繫結至 WCF 資料服務](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)  
  
-   [逐步解說： Silverlight 控制項繫結至 WCF 資料服務](http://msdn.microsoft.com/library/f3f08661-7d91-4185-8ed6-912d524d4c6b)  
  
## <a name="editing-data-in-your-application"></a>在您的應用程式中編輯資料  
 資料呈現給使用者之後，使用者可能會進行加入新資料錄、編輯和刪除資料錄等修改資料的動作，然後再將資料傳送回資料庫。  
  
 如需有關載入您的資料集之後，使用資料的詳細資訊，請參閱[編輯您的應用程式中的資料](../data-tools/editing-data-in-your-application.md)。  
  
## <a name="validating-data"></a>驗證資料  
 變更資料時，通常先要驗證變更，才能允許值送回資料集或寫入資料庫。 *驗證*是程序的名稱，來驗證新值是否可接受的應用程式的需求。 您可以加入邏輯，在應用程式中的值有所變更時查看。 Visual Studio 提供工具可協助加入程式碼，在資料行及資料列變更時驗證資料。 如需詳細資訊，請參閱 <<c0> [ 驗證的資料](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)。  
  
 若要了解如何將資料驗證加入至您的應用程式，請參閱[逐步解說： 將驗證新增至資料集](http://msdn.microsoft.com/library/09351fab-d670-45e3-b53a-a944eff717e7)。  
  
 若要了解如何將驗證新增至其區分為多層式架構應用程式的資料集，請參閱[將驗證新增至多層式架構資料集](../data-tools/add-validation-to-an-n-tier-dataset.md)。  
  
## <a name="saving-data"></a>儲存資料  
 在應用程式變更 (並且驗證這些變更) 之後，通常要將變更送回資料庫。 將資料儲存在資料集中的應用程式，通常會使用 TableAdapterManager 來儲存資料。 如需詳細資訊，請參閱 < [TableAdapterManager 概觀](http://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650)。 Entity Framework 應用程式使用<xref:System.Data.Objects.ObjectContext.SaveChanges%2A>方法來儲存資料。  
  
 如需有關將更新的資料傳送回資料庫的詳細資訊，請參閱 <<c0> [ 儲存資料](../data-tools/saving-data.md)。  
  
 若要了解如何從資料集的更新的資料傳送到資料庫，請完成中的程序[逐步解說： 儲存的資料，從相關資料表 （階層式更新）](http://msdn.microsoft.com/library/50601bd7-a488-480c-9910-3c6570fa3a1b)。  
  
## <a name="related-topics"></a>相關主題  
 [Visual Studio 資料應用程式的概觀](../data-tools/overview-of-data-applications-in-visual-studio.md)  
 提供主題的連結，說明如何建立使用資料的應用程式。  
  
 [連接至 Visual Studio 中的資料](../data-tools/connecting-to-data-in-visual-studio.md)  
 提供有關如何使用的主題連結[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]應用程式連接到資料，並建立您的應用程式的資料來源。  
  
 [準備您的應用程式接收資料](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)  
 包括各項主題連結，說明如何在應用程式中使用資料模型，包括資料集和實體資料模型。  
  
 [將資料擷取至您的應用程式中](../data-tools/fetching-data-into-your-application.md)  
 提供說明如何將資料載入應用程式的主題連結。  
  
 [將控制項繫結至 Visual Studio 中的資料](../data-tools/bind-controls-to-data-in-visual-studio.md)  
 提供主題的連結，說明如何將 Windows Form 控制項、WPF 控制項和 Silverlight 控制項繫結至資料來源。  
  
 [在您的應用程式中編輯資料](../data-tools/editing-data-in-your-application.md)  
 提供說明如何在應用程式中變更資料的主題連結。  
  
 [驗證資料](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)  
 提供說明如何將驗證加入至資料變更的主題連結。  
  
 [儲存資料](../data-tools/saving-data.md)  
 提供主題的連結，說明如何將更新的資料從應用程式傳送至資料庫，或如何以其他格式 (例如 XML) 儲存資料。  
  
 [使用 Visual Studio 中的資料來源的工具](http://msdn.microsoft.com/library/1e584c75-900a-49a0-a82a-d19172ef2eb3)  
 提供可供您使用資料來源，在 Visual Studio 中，而這類工具的相關主題的連結**Zdroje dat**視窗和 ADO.NET 實體資料模型設計工具。