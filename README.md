//Bus seat reservation system
#include <stdio.h>

#define SEATS 20   // total seats in the bus

int main() {
    int seats[SEATS];
    int choice, seatNo;
    for (int i = 0; i < SEATS; i++) {
        seats[i] = 0;
    }
    while (1) {
        printf("\n==== BUS SEAT RESERVATION ====\n");
        printf("1. View Seats\n");
        printf("2. Book Seat\n");
        printf("3. Cancel Seat\n");
        printf("4. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);
        switch (choice) {
        case 1:
            printf("\nSeat Status (0 = Empty, 1 = Booked)\n");
            for (int i = 0; i < SEATS; i++) {
                printf("Seat %2d : %d\n", i + 1, seats[i]);
            }
            break;
        case 2:
            printf("Enter seat number to book (1-20): ");
            scanf("%d", &seatNo);
            if (seatNo < 1 || seatNo > SEATS) {
                printf("Invalid seat number!\n");
            } 
            else if (seats[seatNo - 1] == 1) {
                printf("Seat already booked!\n");
            } 
            else {
                seats[seatNo - 1] = 1;
                printf("Seat %d successfully booked.\n", seatNo);
            }
            break;
        case 3:
            printf("Enter seat number to cancel booking (1-20): ");
            scanf("%d", &seatNo);
            if (seatNo < 1 || seatNo > SEATS) {
                printf("Invalid seat number!\n");
            } 
            else if (seats[seatNo - 1] == 0) {
                printf("Seat is not booked!\n");
            } 
            else {
                seats[seatNo - 1] = 0;
                printf("Seat %d booking cancelled.\n", seatNo);
            }
            break;
        case 4:
            printf("Exiting program...\n");
            return 0;
        default:
            printf("Invalid choice!\n");
        }
    }
    return 0;
}
