from tkinter import*
from tkinter import ttk
from PIL import Image,ImageTk
from tkinter import messagebox
import mysql.connector

 



class Employee:
    def __init__(self,root):
        self.root = root
        self.root.geometry("1530x790+0+0")
        self.root.title('employe management system')

        #variable
        self.var_dep=StringVar()
        self.var_name=StringVar()
        self.var_designation = StringVar()
        self.var_email = StringVar()
        self.var_address=StringVar()
        self.var_married=StringVar()
        self.var_dob=StringVar()
        self.var_doj=StringVar()
        self.var_idproofcombo=StringVar()
        self.var_idproof=StringVar()
        self.var_gender=StringVar()
        self.var_phone=StringVar()
        self.var_country=StringVar()
        self.var_salary=StringVar()




        lbl_title =Label(self.root,text='EMPLOYE MANGEMENT SYSTEM',font=('times new roman',37,'bold','italic'),fg='black',bg='white smoke')
        lbl_title.place(x=0,y=0,width=1530,height=50)
        
       # logo
        img_logo=Image.open('img/logoo.png')
        img_logo=img_logo.resize((50,50),Image.ANTIALIAS)
        self.photo_logo=ImageTk.PhotoImage(img_logo)
        
        self.logo=Label(self.root,image=self.photo_logo)
        self.logo.place(x=300,y=0,width=50,height=50)


#image frame
        img_frame=Frame(self.root,bd=2,relief=RIDGE,bg='white smoke')
        img_frame.place(x=0,y=50,width=1530,height=160)


#image 1st
        img1=Image.open('img/1.jpeg')
        img1=img1.resize((470,160),Image.ANTIALIAS)
        self.photo_first=ImageTk.PhotoImage(img1)
        
        self.first=Label(img_frame,image=self.photo_first)
        self.first.place(x=0,y=0,width=470,height=160)


#image 2nd
        img2=Image.open('img/2.jpg')
        img2=img2.resize((470,160),Image.ANTIALIAS)
        self.photo_second=ImageTk.PhotoImage(img2)


        self.second=Label(img_frame,image=self.photo_second)
        self.second.place(x=470,y=0,width=470,height=160)


#image 3rd
        img3=Image.open('img/3.jpeg')
        img3=img3.resize((470,160),Image.ANTIALIAS)
        self.photo_third=ImageTk.PhotoImage(img3)
        
        self.third=Label(img_frame,image=self.photo_third)
        self.third.place(x=940,y=0,width=470,height=160)


#main frame
        Main_frame=Frame(self.root,bd=4,relief=RIDGE,bg='peachpuff2')
        Main_frame.place(x=10,y=220,width=1380,height=560)


#inner frame 1st
        in1_frame=LabelFrame(Main_frame,bd=4,relief=RIDGE,bg='white smoke',text="employe information",font=('times new roman',11,'bold'),fg='red')
        in1_frame.place(x=10,y=10,width=1380,height=270)


#labels and entry fields
        department=Label(in1_frame,text='Department',font = ('arial',11,'bold'),bg='white smoke')
        department.grid(row=0,column=0,padx=2,sticky=W)

        combo1=ttk.Combobox(in1_frame,textvariable=self.var_dep,font=('arial',12,'bold'),width=17,state='readonly')
        combo1['value']=("select Department",'HR','software engineer ','manager','maintenance')
        combo1.current(0)
        combo1.grid(row=0,column=1,padx=2,pady=10,sticky=W)
#name
        name=Label(in1_frame,font=('arial',12,'bold'),text="NAME",bg='white')
        name.grid(row=0,column=2,padx=2,pady=7)

        txt_name = ttk.Entry(in1_frame,textvariable=self.var_name,width=22,font=('arial',12,'bold'))
        txt_name.grid(row=0,column=3,padx=2,pady=7)


#phone number
        phone=Label(in1_frame,font=('arial',12,'bold'),text="phone no:",bg='white')
        phone.grid(row=0,column=4,padx=2,pady=7)

        txt_phone = ttk.Entry(in1_frame,textvariable=self.var_phone,width=22,font=('arial',12,'bold'))
        txt_phone.grid(row=0,column=5,padx=2,pady=7)


#designation
        designation=Label(in1_frame,font=('arial',12,'bold'),text="DESIGNATION",bg='white')
        designation.grid(row=1,column=0,padx=2,pady=7)

        txt_designation = ttk.Entry(in1_frame,textvariable=self.var_designation,width=17,font=('arial',12,'bold'))
        txt_designation.grid(row=1,column=1,padx=2,pady=7)


#email
        email=Label(in1_frame,font=('arial',12,'bold'),text="EMAIL",bg='white')
        email.grid(row=1,column=2,padx=2,pady=7)

        txt_email = ttk.Entry(in1_frame,textvariable=self.var_email,width=22,font=('arial',12,'bold'))
        txt_email.grid(row=1,column=3,padx=2,pady=7)

#country
        country=Label(in1_frame,font=('arial',12,'bold'),text="country",bg='white')
        country.grid(row=1,column=4,padx=2,pady=7)

        txt_country = ttk.Entry(in1_frame,textvariable=self.var_country,width=22,font=('arial',12,'bold'))
        txt_country.grid(row=1,column=5,padx=2,pady=7)


#address
        address=Label(in1_frame,font=('arial',12,'bold'),text="Address",bg='white')
        address.grid(row=2,column=0,padx=2,pady=7)

        txt_address = ttk.Entry(in1_frame,textvariable=self.var_address,width=22,font=('arial',12,'bold'))
        txt_address.grid(row=2,column=1,padx=2,pady=7)

#married status
        Maried_status=Label(in1_frame,text='Maried status',font = ('arial',11,'bold'),bg='white smoke')
        Maried_status.grid(row=2,column=2,padx=2)

        combo2=ttk.Combobox(in1_frame,textvariable=self.var_married,font=('arial',12,'bold'),width=17,state='readonly')
        combo2['value']=("Maried Staus",'Maried','Un Maried ','widow','divorced')
        combo2.current(0)
        combo2.grid(row=2,column=3,padx=2,pady=10)

#salary
        salary=Label(in1_frame,font=('arial',12,'bold'),text="salary",bg='white')
        salary.grid(row=2,column=4,padx=2,pady=7)

        txt_salary = ttk.Entry(in1_frame,textvariable=self.var_salary,width=22,font=('arial',12,'bold'))
        txt_salary.grid(row=2,column=5,padx=2,pady=7)

#dob:
        dob=Label(in1_frame,font=('arial',12,'bold'),text="DOB:",bg='white')
        dob.grid(row=3,column=0,padx=2,pady=7)

        txt_dob = ttk.Entry(in1_frame,textvariable=self.var_dob,width=22,font=('arial',12,'bold'))
        txt_dob.grid(row=3,column=1,padx=2,pady=7)

#doj:   
        doj=Label(in1_frame,font=('arial',12,'bold'),text="DOJ:",bg='white')
        doj.grid(row=3,column=2,padx=2,pady=7)

        txt_doj = ttk.Entry(in1_frame,textvariable=self.var_doj,width=22,font=('arial',12,'bold'))
        txt_doj.grid(row=3,column=3,padx=2,pady=7)


#select id 
        combo3=ttk.Combobox(in1_frame,textvariable=self.var_idproofcombo,font=('arial',12,'bold'),width=17,state='readonly')
        combo3['value']=("Select id proof",'adhar card','pan card ','driving licence','passport','janadhar')
        combo3.current(0)
        combo3.grid(row=4,column=0,padx=2,pady=10)

        txt_id = ttk.Entry(in1_frame,textvariable=self.var_idproof,width=22,font=('arial',12,'bold'))
        txt_id.grid(row=4,column=1,padx=2,pady=7)


#gender
        gender=Label(in1_frame,font=('arial',12,'bold'),text="gender:",bg='white')
        gender.grid(row=4,column=2,padx=2,pady=7)

        combo4=ttk.Combobox(in1_frame,textvariable=self.var_gender,font=('arial',12,'bold'),width=17,state='readonly')
        combo4['value']=("select gender",'male','female ','bisexual','homo','transgender')
        combo4.current(0)
        combo4.grid(row=4,column=3,padx=2,pady=10)

#image
       #
       # img4=Image.open('img/forth.jpg')
        #img4=img4.resize((220,220),Image.ANTIALIAS)
        #self.photo_fourth=ImageTk.PhotoImage(img4)
        
        #self.fourth=Label(in1_frame,image=self.photo_fourth)
        #self.fourth.place(x=1200,y=0,width=220,height=220)
#button frame
        fbutton=Frame(in1_frame,bd=4,relief=RIDGE,bg='peachpuff2')
        fbutton.place(x=1100,y=20,width=170,height=210)
 
 
#button save
        badd=Button(fbutton,text="save",command=self.add_data,font=("arial",15,'bold'),width=13,bg='grey',fg='black')
        badd.grid(row=0, column=0, padx=1,pady=5)

#button update
        bupdate=Button(fbutton,text="update",command=self.update_data,font=("arial",15,'bold'),width=13,bg='grey',fg='black')
        bupdate.grid(row=1, column=0, padx=1,pady=5)


#button delete
        bdelete=Button(fbutton,text="delete",command=self.delete_data,font=("arial",15,'bold'),width=13,bg='grey',fg='black')
        bdelete.grid(row=2, column=0, padx=1,pady=5)


#button reset
        breset=Button(fbutton,text="reset",command=self.reset_data,font=("arial",15,'bold'),width=13,bg='grey',fg='black')
        breset.grid(row=3, column=0, padx=1,pady=5)



        



#lower frame 2nd
        lower_frame=LabelFrame(Main_frame,bd=4,relief=RIDGE,bg='white smoke',text="employe information table",font=('times new roman',11,'bold'),fg='red')
        lower_frame.place(x=10,y=280,width=1380,height=270)


#lower1 frame 2nd
        lower_frame1=LabelFrame(lower_frame,bd=4,relief=RIDGE,bg='white smoke',text="Search Employe information",font=('times new roman',11,'bold'),fg='red')
        lower_frame1.place(x=0,y=0,width=1380,height=60)






# lower frame 1st item       
        searchby=Label(lower_frame1,font=('arial',12,'bold'),text="search by:",bg='red',fg='white')
        searchby.grid(row=0,column=0,padx=2,pady=2)


    # search option
        self.var_com_search=StringVar()
        combo5=ttk.Combobox(lower_frame1,textvariable=self.var_com_search,font=('arial',12,'bold'),width=17,state='readonly')
        combo5['value']=("select option",'phone','id proof')
        combo5.current(0)
        combo5.grid(row=0,column=1,padx=2,pady=0)


    #entery
        self.var_search=StringVar()

        txt_id = ttk.Entry(lower_frame1,textvariable=self.var_search,width=22,font=('arial',12,'bold'))
        txt_id.grid(row=0,column=2,padx=2,pady=0)

    #  button serach
        bsearch=Button(lower_frame1,text="search",command=self.search_data,font=("arial",15,'bold'),width=13,bg='grey',fg='black')
        bsearch.grid(row=0, column=3, padx=1,pady=0)    

    #button show all
        bshow=Button(lower_frame1,text="show all",command=self.fetch_data,font=("arial",15,'bold'),width=13,bg='grey',fg='black')
        bshow.grid(row=0, column=4, padx=1,pady=0)
    
    # lable 

        wearmask=Label(lower_frame1,font=('times new roman',30,'bold'),text="wear mask",fg='blue')
        wearmask.grid(row=0,column=5,padx=202,pady=0)


#=======================================employe table============================================
    # frame 2 :-
        table_frame=Frame(lower_frame,bd=4,relief=RIDGE)
        table_frame.place(x=0,y=70,width=1380,height=210)

    #scrool bar 
        scrollx = ttk.Scrollbar(table_frame,orient=HORIZONTAL)
        scrolly = ttk.Scrollbar(table_frame,orient=VERTICAL)

        self.employee_table=ttk.Treeview(table_frame,column=("dep","name","degi","email","address","married","dob","doj","idpoofcombo","idproof","gender","phone","country","salary"),xscrollcommand=scrollx.set,yscrollcommand=scrolly.set)

        scrollx.pack(side=TOP,fill=X)
        scrolly.pack(side=LEFT,fill=Y)

        scrollx.config(command=self.employee_table.xview)
        scrolly.config(command=self.employee_table.yview)

        self.employee_table.heading('dep',text="Department")
        self.employee_table.heading('name',text="Name")
        self.employee_table.heading('degi',text="Degignation")
        self.employee_table.heading('email',text="Email")
        self.employee_table.heading('address',text="address")
        self.employee_table.heading('married',text="Married status")
        self.employee_table.heading('dob',text="DOB")
        self.employee_table.heading('doj',text="DOJ")
        self.employee_table.heading('idpoofcombo',text="ID TYPE")
        self.employee_table.heading('idproof',text="ID NUMBER")
        self.employee_table.heading('gender',text="Gender")
        self.employee_table.heading('phone',text="Phone no")
        self.employee_table.heading('country',text="Country")
        self.employee_table.heading('salary',text="Salary")

        self.employee_table['show']='headings'

        self.employee_table.column("dep", width=100)
        self.employee_table.column("name", width=100)
        self.employee_table.column("degi", width=100)
        self.employee_table.column("email", width=100)
        self.employee_table.column("address",width=100)
        self.employee_table.column("married", width=100)
        self.employee_table.column("dob", width=100)
        self.employee_table.column("doj", width=100)
        #self.employee_table.column("idproofcombo", width=100)
        self.employee_table.column("idproof", width=100)
        self.employee_table.column("gender", width=100)
        self.employee_table.column("phone", width=100)
        self.employee_table.column("country", width=100)
        self.employee_table.column("salary", width=100)
       
        
        


        self.employee_table.pack(fill=BOTH,expand=1)
        
        self.employee_table.bind("<ButtonRelease>",self.get_cursor)

        self.fetch_data()

    #=========================function declaration============================
        
    def add_data(self):
        if self.var_dep.get()=="" or self.var_email.get()=="":
            messagebox.showerror('error ','all fields are required')
        else:
            try:
                conn=mysql.connector.connect(host = 'localhost',database='employee',user="root",password='root')
                my_cursor=conn.cursor()
                

                my_cursor.execute('insert into employee1 values( %s, %s, %s ,%s ,%s ,%s ,%s ,%s ,%s ,%s ,%s ,%s ,%s ,%s)',(

                                                                                                self.var_dep.get(),
                                                                                                self.var_name.get(),
                                                                                                self.var_designation.get(),
                                                                                                self.var_email.get(),
                                                                                                self.var_address.get(),
                                                                                                self.var_married.get(),
                                                                                                self.var_dob.get(),
                                                                                                self.var_doj.get(),
                                                                                                self.var_idproofcombo.get(),
                                                                                                self.var_idproof.get(),
                                                                                                self.var_gender.get(),
                                                                                                self.var_phone.get(),
                                                                                                self.var_country.get(),
                                                                                                self.var_salary.get()
                                                                                                ) )
                conn.commit()
                conn.close()      
                messagebox.showinfo('success','employee has been added',parent=self.root)
                self.fetch_data()
                
                
            except Exception as es:
                    messagebox.showerror('error',f'Due to:{str(es)}',parent=self.root)                                                                                    

       
        #fetch data
    def fetch_data(self):
        conn=mysql.connector.connect(host='localhost',user ='root',password='root',database='employee')
        my_cursor=conn.cursor()
        my_cursor.execute('select*from employee1')
        data=my_cursor.fetchall()
        if len(data)!= 0:
                self.employee_table.delete(*self.employee_table.get_children())
                for i in data:
                        self.employee_table.insert("",END,values=i)
                conn.commit()
        conn.close()
       
    #getcursor
    def get_cursor(self,event=""):
            cursor_row=self.employee_table.focus()
            content=self.employee_table.item(cursor_row)
            data=content['values']


            self.var_dep.set(data[0])
            self.var_name.set(data[1])
            self.var_designation.set(data[2])
            self.var_email.set(data[3])
            self.var_address.set(data[4])
            self.var_married.set(data[5])
            self.var_dob.set(data[6])
            self.var_doj.set(data[7])
            self.var_idproofcombo.set(data[8])
            self.var_idproof.set(data[9])
            self.var_gender.set(data[10])
            self.var_phone.set(data[11])
            self.var_country.set(data[12])
            self.var_salary.set(data[13])
    
    def update_data(self):
        if self.var_dep.get()=="" or self.var_email.get()=="":
            messagebox.showerror('error ','all fields are required')
        else:
            try:
                update=messagebox.askyesno('update','are you sure to update this data')
                if update>0:

                    conn=mysql.connector.connect(host = 'localhost',database='employee',user="root",password='root')
                    my_cursor=conn.cursor()
                    my_cursor.execute('update employee1 set department=%s,name=%s,designation=%s,email=%s, address=%s, married_status=%s, dob=%s, doj=%s, id_proof_type=%s, gender=%s, phone=%s,employee1col=%s, salary=%s where id_proof=%s',(
                                                                                                self.var_dep.get(),
                                                                                                self.var_name.get(),
                                                                                                self.var_designation.get(),
                                                                                                self.var_email.get(),
                                                                                                self.var_address.get(),
                                                                                                self.var_married.get(),
                                                                                                self.var_dob.get(),
                                                                                                self.var_doj.get(),
                                                                                                self.var_idproofcombo.get(),
                                                                                                
                                                                                                self.var_gender.get(),
                                                                                                self.var_phone.get(),
                                                                                                self.var_country.get(),
                                                                                                self.var_salary.get() ,
                                                                                                self.var_idproof.get()                                                                                                                                

                    ))
                else:
                    if not update:
                            return
                conn.commit()
                self.fetch_data()
                conn.close()
                messagebox.showinfo('success','employee succesfully updated',parent=self.root)
            except Exception as es:
                    messagebox.showerror('error',f'Due to:{str(es)}',parent=self.root)         


    #delete function
    def delete_data(self):
            if self.var_idproof.get()=="":
                    messagebox.showerror("error",'all fields are required')
            else:
                try:
                    delete=messagebox.askyesno("Delete","are you sure delete this employee data",parent=self.root) 
                    if delete>0:
                            
                        conn=mysql.connector.connect(host = 'localhost',database='employee',user="root",password='root')
                        my_cursor=conn.cursor()
                        sql='delete from employee1 where id_proof=%s'
                        value=(self.var_idproof.get(),)
                        my_cursor.execute(sql,value)
                    else:
                        if not delete:
                                return
                    conn.commit()
                    self.fetch_data()
                    conn.close()
                    messagebox.showinfo('success','employee succesfully deleted',parent=self.root)
                except Exception as es:
                    messagebox.showerror('error',f'Due to:{str(es)}',parent=self.root)         

    #reset button
    def reset_data(self):
        self.var_dep.set("select department")
        self.var_name.set("")
        self.var_designation.set("")
        self.var_email.set("")
        self.var_address.set("")
        self.var_married.set("married status")
        self.var_dob.set("")
        self.var_doj.set("")
        self.var_idproofcombo.set("select id proof")
        self.var_idproof.set("")
        self.var_gender.set("")
        self.var_phone.set("")
        self.var_country.set("")
        self.var_salary.set("")
    #search
    def search_data(self):
        if self.var_com_search.get()=='' or self.var_search.get()=='':
            messagebox.showerror('error','please select option')
        else:
            try:
                conn=mysql.connector.connect(host = 'localhost',database='employee',user="root",password='root')
                my_cursor=conn.cursor()
                my_cursor.execute('select * from employee1 where ' +str(self.var_com_search.get())+" LIKE '%"+str(self.var_search.get()+"%'") )
                rows=my_cursor.fetchall()
                if len(rows)!=0:
                    self.employee_table.delete(*self.employee_table.get_children())
                    for i in rows:
                        self.employee_table.insert("",END,values=i)
                    conn.commit()
                conn.close()
            except Exception as es:
                    messagebox.showerror('error',f'Due to:{str(es)}',parent=self.root)   



       

if __name__=="__main__":
    root = Tk()
    obj=Employee(root)
    root.mainloop()