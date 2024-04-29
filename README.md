⚠Project has been completed and will not recieve changes.⚠


> [!NOTE]
> # Scenario[^1]

[^1]: I have been hired by the Artemis Hotel to create a hotel management system. The system will be used by the hotel for managing customers bookings and their details. The program system must be capable of providing the following information: Hotel Booking, Provides Hotel Rooms Info, Room Service, Billing and Record-Keeping.


> [!NOTE]
> # Methods[^2]

[^2]: · Analyse the detailed requirements using suitable methods, i.e. analysis by decomposition of requirements (breaking down the tasks into manageable parts). Elements and functions table. Algorithms / pseudocode or flow diagram. Show the iterative development of the individual solutions with suitable testing throughout the process. Test the final product with an appropriate test table and evaluate the solution against the detailed requirements Iidentified in the analysis.


> [!NOTE]
> # System Requirements[^3]

[^3]: · Main Menu options Personal details: including type of room and service booked.Hotel room details: Type of room, number of persons, number of beds, what is included in the room i.e. on-suite, couch, TV etc. Bookings. Billing and payments. Record keeping guest records, guests and allocated rooms, vacancy of rooms, room services. Database CSV document for customer / guests’ details. Test table to show that the system works.


> [!IMPORTANT]
> # Extras[^4]
[^4]: · The code for the hotel system uses a Csv file to import its information.

> [!Warning]
> # Code Used


Import csv

Def load_customer_data(file_path):

With open(file_path, ‘r’) as file:

Reader = csv.DictReader(file)

Return list(reader)

Def load_hotel_room_data(file_path):

With open(file_path, ‘r’) as file:

Reader = csv.DictReader(file)

Return list(reader)

Def main_menu():

Print(“Welcome to Artemis Hotel Management System”)

Print(“1. Personal details”)

Print(“2. Hotel room details”)

Print(“3. Bookings”)

Print(“4. Billing and payments”)

Print(“5. Record keeping”)

Print(“6. Exit”)

Def display_room_details(room_data):

Print(“Room\tPrice per night\tOccupied”)

For i, price in enumerate(room_data, start=1):

Print(f”{i}\t{price[‘PricePerNight’]}\t\t{price[‘Occupied’]}”)

Def handle_personal_details(customer_data):

Print(“Enter customer details:”)

Name = input(“Name: “)

Room_number = input(“Room number: “)

Amount_paid = input(“Amount Paid: “)

Phone_number = input(“Phone number: “)

Customer_data.append({

‘Name’: name,

‘Room number’: room_number,

‘Amount Paid’: amount_paid,

‘Phone number’: phone_number

})

Print(“Customer details added successfully.”)

Def handle_bookings(room_data):

Room_number = input(“Enter room number to book: “)

Try:

Room_number = int(room_number)

If 1 <= room_number <= len(room_data):

If room_data[room_number – 1][‘Occupied’] == ‘No’:

Room_data[room_number – 1][‘Occupied’] = ‘Yes’

Print(f”Room {room_number} booked successfully.”)

Else:

Print(f”Room {room_number} is already occupied.”)

Else:

Print(“Invalid room number.”)

Except ValueError:

Print(“Invalid input. Please enter a valid room number.”)

Def handle_billing_and_payments(customer_data):

Room_number = input(“Enter room number to generate bill: “)

For customer in customer_data:

If customer[‘Room number’] == room_number:

Print(f”Name: {customer[‘Name’]}”)

Print(f”Room number: {customer[‘Room number’]}”)

Print(f”Amount Paid: {customer[‘Amount Paid’]}”)

Print(f”Phone number: {customer[‘Phone number’]}”)

Return

Print(“No customer found with the given room number.”)

Def handle_record_keeping(customer_data, room_data):

Print(“Customer Records:”)

For customer in customer_data:

Print(customer)

Print(“\nHotel Room Records:”)

Display_room_details(room_data)

Customer_data = load_customer_data(‘Customer.csv’)

Room_data = load_hotel_room_data(‘Hotelinfo.csv’)

While True:

Main_menu()

Choice = input(“Enter your choice: “)

If choice == ‘1’:

Handle_personal_details(customer_data)

Elif choice == ‘2’:

Display_room_details(room_data)

Elif choice == ‘3’:

Handle_bookings(room_data)

Elif choice == ‘4’:

Handle_billing_and_payments(customer_data)

Elif choice == ‘5’:

Handle_record_keeping(customer_data, room_data)

Elif choice == ‘6’:

Print(“Exiting...”)

Break

Else:

Print(“Invalid choice. Please try again.”)

