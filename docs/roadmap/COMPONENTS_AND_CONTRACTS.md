# Components and Contracts

## Domain entities
- `PoliceTrip`
- `TripParticipant`
- `Driver`
- `DriverContact`
- `VehicleAssignment`
- `VehicleResponsibility`

## Repository interfaces
```ts
interface PoliceTripRepository {
  create(trip: PoliceTrip, participants: TripParticipant[]): Promise<void>;
  findByDate(date: string): Promise<PoliceTrip[]>;
  findByPeriod(from: string, to: string): Promise<PoliceTrip[]>;
  findByDriver(driverId: string): Promise<PoliceTrip[]>;
}

interface DriverRepository {
  getById(driverId: string): Promise<Driver | null>;
  searchActive(query: string): Promise<Driver[]>;
}

interface ContactRepository {
  getByDriverId(driverId: string): Promise<DriverContact[]>;
}

interface AssignmentRepository {
  findAtDate(driverId: string, date: string): Promise<VehicleAssignment | null>;
}

interface SupervisorRepository {
  findByBoardCode(boardCode: string): Promise<VehicleResponsibility | null>;
}
```

## Application services
- `TripService` - trip CRUD/query use cases.
- `RouteService` - deterministic city and participant order.
- `AssignmentService` - assignment on target date.
- `ParticipantResolutionService` - final operational participant view.
- `MessageGeneratorService` - manager/driver text.

Messages are derived output in MVP, not persistent business entities.