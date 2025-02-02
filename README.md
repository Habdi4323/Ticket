tickets = {}
ticket_counter = 1  


def create_ticket():
    global ticket_counter  
    description = input("Enter ticket description: ")
    priority = input("Enter ticket priority (Low, Medium, High): ")
    
    
  ticket_id = ticket_counter
    tickets[ticket_id] = {
        'description': description,
        'priority': priority,
        'status': 'Open'
    }
    ticket_counter += 1  
    print(f"Ticket {ticket_id} created successfully.\n")


def view_tickets():
    if len(tickets) == 0:
        print("No tickets available.\n")
    else:
        for ticket_id, info in tickets.items():
            print(f"Ticket ID: {ticket_id} | Description: {info['description']} | Status: {info['status']} | Priority: {info['priority']}")
        print()


def update_ticket():
    ticket_id = int(input("Enter ticket ID to update: "))
    if ticket_id in tickets:
        new_status = input("Enter new status (Open, In Progress, Resolved): ")
        tickets[ticket_id]['status'] = new_status
        print(f"Ticket {ticket_id} updated to {new_status}.\n")
    else:
        print(f"Ticket {ticket_id} not found.\n")


def delete_ticket():
    ticket_id = int(input("Enter ticket ID to delete: "))
    if ticket_id in tickets:
        del tickets[ticket_id]
        print(f"Ticket {ticket_id} deleted.\n")
    else:
        print(f"Ticket {ticket_id} not found.\n")


def main_menu():
    while True:
        print("IT Ticketing System")
        print("1. Create Ticket")
        print("2. View Tickets")
        print("3. Update Ticket Status")
        print("4. Delete Ticket")
        print("5. Exit")
        
        
  choice = input("Enter your choice (1-5): ").strip()
        print(f"Debug: You entered choice '{choice}'")  

  if choice == '1':
            create_ticket()
        elif choice == '2':
            view_tickets()
        elif choice == '3':
            update_ticket()
        elif choice == '4':
            delete_ticket()
        elif choice == '5':
            print("Exiting the system. Goodbye!")
            break
        else:
            print("Invalid choice. Please enter a number between 1 and 5.\n")


main_menu()
