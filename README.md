# 学员管理系统 demo

def welcome():
    print("欢迎使用学员管理系统")
    print("1. 添加学员")
    print("2. 查看所有学员")
    print("3. 学员人数统计")
    print("4. 保存学员到文件")
    print("5. 从文件加载学员")
    print("0. 退出系统")

students = []  # 用列表保存学员信息

def add_student():
    name = input("请输入学员姓名: ")
    age = int(input("请输入学员年龄: "))
    score = float(input("请输入学员成绩: "))
    student = {"name": name, "age": age, "score": score}
    students.append(student)
    print(f"学员{name}添加成功！")

def show_students():
    if not students:
        print("当前没有学员信息。")
    else:
        for idx, stu in enumerate(students):
            print(f"{idx+1}. 姓名:{stu['name']} 年龄:{stu['age']} 成绩:{stu['score']}")

def count_students():
    print(f"当前学员总人数: {len(students)}")

def save_students():
    try:
        with open("students.txt", "w", encoding="utf-8") as f:
            for stu in students:
                line = f"{stu['name']},{stu['age']},{stu['score']}\n"
                f.write(line)
        print("保存成功！")
    except Exception as e:
        print("保存失败:", e)

def load_students():
    try:
        with open("students.txt", "r", encoding="utf-8") as f:
            students.clear()
            for line in f:
                name, age, score = line.strip().split(",")
                student = {"name": name, "age": int(age), "score": float(score)}
                students.append(student)
        print("加载成功！")
    except Exception as e:
        print("加载失败:", e)

def main():
    while True:
        welcome()
        choice = input("请选择操作（输入序号）: ")
        if choice == "1":
            add_student()
        elif choice == "2":
            show_students()
        elif choice == "3":
            count_students()
        elif choice == "4":
            save_students()
        elif choice == "5":
            load_students()
        elif choice == "0":
            print("退出系统。")
            break
        else:
            print("输入有误，请重新选择。")

if __name__ == "__main__":
    main()
