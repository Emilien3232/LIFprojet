## Structure du projet

\```text
Assets/
├── Scenes/
│   └── Entrepot.unity
├── Prefabs/
│   ├── Robot.prefab
│   └── ZoneStock.prefab
├── Materials/
├── NavMesh/                      # NavMeshSurface bakée, off-mesh links custom
├── Scripts/
│   ├── Warehouse/                # Modèle de l'entrepôt (allées, zones, adressage A[n]-Z-[m])
│   │   ├── WarehouseGrid.cs
│   │   └── StockZone.cs
│   ├── Orders/                   # Une commande = liste de pièces à récupérer
│   │   ├── Order.cs
│   │   └── OrderItem.cs
│   ├── TaskSystem/                # Décomposition commande → tâches
│   │   ├── Task.cs                # ex: PickupTask, CarryHeavyItemTask
│   │   ├── TaskDecomposer.cs      # Order → liste de Task
│   │   └── TaskAllocator.cs       # Task → Robot (allocation distribuée / enchères)
│   ├── Coalition/                 # Formation de coalitions pour items lourds
│   │   └── CoalitionManager.cs
│   ├── Robots/
│   │   ├── RobotController.cs     # Wrapper autour de NavMeshAgent
│   │   ├── RobotState.cs          # idle, moving, carrying, docking...
│   │   └── RobotIdManager.cs      # Gestion des ré-attributions R1..Rn au retour
│   └── Navigation/
│       ├── OneWayLaneRule.cs      # Contrainte montant/descendant sur An/An+1
│       └── ZoneAccessRule.cs      # Accès pair/impair gauche/droite
└── Editor/
\```
