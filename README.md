Plan prevision:

Assets/
├── Scenes/
│   └── Entrepot.unity
├── Prefabs/
│   ├── Robot.prefab
│   └── ZoneStock.prefab
├── Materials/
├── NavMesh/                     ← NavMeshSurface bakée, off-mesh links custom
├── Scripts/
│   ├── Warehouse/               ← modèle de l'entrepôt (allées, zones, adressage A[n]-Z-[m])
│   │   ├── WarehouseGrid.cs
│   │   └── StockZone.cs
│   ├── Orders/                  ← une commande = liste de pièces à récupérer
│   │   ├── Order.cs
│   │   └── OrderItem.cs
│   ├── TaskSystem/               ← décomposition commande → tâches
│   │   ├── Task.cs               (ex: PickupTask, CarryHeavyItemTask)
│   │   ├── TaskDecomposer.cs     (Order → liste de Task)
│   │   └── TaskAllocator.cs      (Task → Robot, ex. allocation distribuée/enchères)
│   ├── Coalition/                ← formation de coalitions pour items lourds
│   │   └── CoalitionManager.cs
│   ├── Robots/
│   │   ├── RobotController.cs    (wrapper autour de NavMeshAgent)
│   │   ├── RobotState.cs         (idle, moving, carrying, docking...)
│   │   └── RobotIdManager.cs     (gestion des ré-attributions R1..Rn au retour)
│   └── Navigation/
│       ├── OneWayLaneRule.cs     (contrainte montant/descendant sur An/An+1)
│       └── ZoneAccessRule.cs     (accès pair/impair gauche/droite)
└── Editor/    
