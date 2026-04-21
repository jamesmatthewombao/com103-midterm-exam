chores = {
    1: {"name": "Sweeping / Mopping", "schedule": "Daily"},
    2: {"name": "Dishwashing", "schedule": "After meals"},
    3: {"name": "Taking Out Trash", "schedule": "Every other day"},
    4: {"name": "Cleaning Bathroom", "schedule": "Weekly"},
    5: {"name": "Buying Groceries", "schedule": "Weekly"}
}

room_monitor = input("Room monitor name: ")
room_number = input("Room number: ")

assigned = []

print("\n==========================================")
print("        DORM ROOM -- CHORE LIST")
print("==========================================")

for num, chore in chores.items():
    print(f"{num}. {chore['name']} [{chore['schedule']}]")

print("==========================================")

for i in range(1, 6):
    print(f"\n--- CHORE {i} ---")
    try:
        choice = int(input("Chore number (0 to skip): "))
    except:
        choice = 0

    if choice == 0:
        continue

    if choice in chores:
        name = input("Roommate name: ")
        status = input("Status (done/not done): ")

        assigned.append({
            "chore": chores[choice]["name"],
            "schedule": chores[choice]["schedule"],
            "name": name,
            "status": status.lower()
        })

print("\n=============================================")
print(f"     ROOM {room_number} -- WEEKLY CHORE REPORT")
print("=============================================")
print(f"Room Monitor : {room_monitor}")
print("---------------------------------------------")

done_count = 0

for i, task in enumerate(assigned, 1):
    print(f"[{i}] {task['chore']} [{task['schedule']}]")
    print(f"    Roommate : {task['name']}")
    print(f"    Status   : {task['status']}\n")

    if task['status'] == "done":
        done_count += 1

total = len(assigned)

if total > 0:
    rate = (done_count / total) * 100
else:
    rate = 0

print("---------------------------------------------")
print(f"Completed      : {done_count} out of {total} assigned")
print(f"Completion Rate: {rate:.0f}%")

if rate == 100:
    status = "EXCELLENT!"
elif rate >= 75:
    status = "GOOD JOB!"
elif rate >= 50:
    status = "ALMOST THERE!"
else:
    status = "NEEDS IMPROVEMENT!"

print(f"Room Status    : {status}")
print("=============================================")

