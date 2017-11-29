---
title: TcpTransportBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 33bbc1e5-44e4-4ee3-b7b5-801dc78956e4
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 180e954661319cb32edfd3180418fe9b1571ea5c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="tcptransportbindingelement"></a><span data-ttu-id="bf842-102">TcpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="bf842-102">TcpTransportBindingElement</span></span>
<span data-ttu-id="bf842-103">TcpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="bf842-103">TcpTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf842-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bf842-104">Syntax</span></span>  
  
```  
class TcpTransportBindingElement : ConnectionOrientedTransportBindingElement  
{  
  TcpConnectionPoolSettings ConnectionPoolSettings;  
  sint32 ListenBacklog;  
  boolean PortSharingEnabled;  
  boolean TeredoEnabled;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="bf842-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="bf842-105">Methods</span></span>  
 <span data-ttu-id="bf842-106">A classe TcpTransportBindingElement não define nenhum método.</span><span class="sxs-lookup"><span data-stu-id="bf842-106">The TcpTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="bf842-107">Propriedades</span><span class="sxs-lookup"><span data-stu-id="bf842-107">Properties</span></span>  
 <span data-ttu-id="bf842-108">A classe TcpTransportBindingElement tem as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="bf842-108">The TcpTransportBindingElement class has the following properties:</span></span>  
  
### <a name="connectionpoolsettings"></a><span data-ttu-id="bf842-109">ConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="bf842-109">ConnectionPoolSettings</span></span>  
 <span data-ttu-id="bf842-110">Tipo de dados: TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="bf842-110">Data type: TcpConnectionPoolSettings</span></span>  
  
 <span data-ttu-id="bf842-111">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="bf842-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bf842-112">As configurações de pool de conexão.</span><span class="sxs-lookup"><span data-stu-id="bf842-112">The connection pool settings.</span></span>  
  
### <a name="listenbacklog"></a><span data-ttu-id="bf842-113">ListenBacklog</span><span class="sxs-lookup"><span data-stu-id="bf842-113">ListenBacklog</span></span>  
 <span data-ttu-id="bf842-114">Tipo de dados: sint32</span><span class="sxs-lookup"><span data-stu-id="bf842-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="bf842-115">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="bf842-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bf842-116">O número máximo de solicitações de conexão em fila que podem estar pendentes.</span><span class="sxs-lookup"><span data-stu-id="bf842-116">The maximum number of queued connection requests that can be pending.</span></span>  
  
### <a name="portsharingenabled"></a><span data-ttu-id="bf842-117">portSharingEnabled</span><span class="sxs-lookup"><span data-stu-id="bf842-117">PortSharingEnabled</span></span>  
 <span data-ttu-id="bf842-118">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="bf842-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="bf842-119">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="bf842-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bf842-120">Um valor booleano que especifica se o compartilhamento de porta TCP está habilitado para esta conexão.</span><span class="sxs-lookup"><span data-stu-id="bf842-120">A boolean value that specifies whether TCP port sharing is enabled for this connection.</span></span>  
  
### <a name="teredoenabled"></a><span data-ttu-id="bf842-121">teredoEnabled</span><span class="sxs-lookup"><span data-stu-id="bf842-121">TeredoEnabled</span></span>  
 <span data-ttu-id="bf842-122">Tipo de dados: boolean</span><span class="sxs-lookup"><span data-stu-id="bf842-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="bf842-123">Tipo de acesso: somente leitura</span><span class="sxs-lookup"><span data-stu-id="bf842-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bf842-124">Um valor booleano que especifica se Teredo (uma tecnologia para endereçar cliente que estão atrás de firewalls) está habilitado.</span><span class="sxs-lookup"><span data-stu-id="bf842-124">A boolean value that specifies whether Teredo (a technology for addressing clients that are behind firewalls) is enabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf842-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bf842-125">Requirements</span></span>  
  
|<span data-ttu-id="bf842-126">MOF</span><span class="sxs-lookup"><span data-stu-id="bf842-126">MOF</span></span>|<span data-ttu-id="bf842-127">Declarado em Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="bf842-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="bf842-128">Namespace</span><span class="sxs-lookup"><span data-stu-id="bf842-128">Namespace</span></span>|<span data-ttu-id="bf842-129">Definido em root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="bf842-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bf842-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bf842-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>