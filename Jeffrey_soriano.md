This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...

Creating Doctors appointment rework project

Create rails file
- first I opened the terminal then changed directory to desktop 
- then I created a new rails file using the rails new name -d postgresql command
- cd into the new file you created
- I used the command "code ." once inside to open the new rails file. 

Add gems
- go to gemfile and add all the gems you need to the development section
- bundle install in the terminal

Create models 
- first db:create to create a new database
- now create some of the models you'll need
- rails g model doctor name 
- rails g model patient name
- rails g model appointment patient:belongs_to doctor:belongs_to date:datetime
- adding the belongs to creates columns that link your models example "patient_id"
- now is a good time to stage your code
- git add . 
- git commit -m 'initial files, added models'

Add associations 
- open doctor.rb
- add: 
has_many :appointments
has_many :patients through: :appointments
- open patient.rb
- add: 
has_many :appointments
has_many :doctors through: :appointments

Create controllers
- rails g controller *name_plural* index show new edit for all CRUD actions

Route controllers
- open routes
- add:
root 'doctors#index'

  resources :patients

  resources :doctors do 
    resources :appointments
  end
- not going to nest appointments yet because i want to create CRUD actions for these first

Run server
- now would be a good time to see if its all working
- rails server or rails s in a new terminal window in the correct file
- now got to local host 30000

Open controller 
- open doctor controller to get all the CRUD actions working
- i like to just add all the methods ill need and the begning and before action:

class DoctorsController < ApplicationController
  before_action :set_doctor, only: [:show, :edit, :update, :destroy]

  def index
    @doctors = Doctor.all
  end

  def show
  end

  def new
  end

  def create 
  end

  def edit
  end

  def update
  end

  def destroy
  end

  private

  def set_doctor
    @doctor = Doctor.find(params[:id])
  end

  def doctor_params
    params.require(:doctor).permit(:name)
  end

end

display all doctors
- open doctors index
<h1>Doctors</h1>
<% @doctors.each do |doctor| %>
    <%= doctor.name %>
    <%= link_to 'Show appointments', doctor_path(doctor) %>
    <%= link_to 'Edit doctor', edit_doctor_path(doctor) %>
    <%= link_to 'Delete doctor', doctor, method: :delete %>
<% end %>

<h2>Create New Doctor</h2>
<%= link_to 'New Doctor', new_doctor_path%>

- created a loop for each doctor in the data base to create, show , delete, and edit 

Using faker and the seed to create fake data to go in
- open seeds.rb
- added: require 'faker'

10.times do 
    @doc = Doctor.create( name: Faker::Name.last_name)
end

- to add fake data into the data base for doctors (we'll come back :) )

- complete the Crud for doctors:
class DoctorsController < ApplicationController
  before_action :set_doctor, only: [:show, :edit, :update, :destroy]

  def index
    @doctors = Doctor.all
  end

  def show
  end

  def new
    @doctor = Doctor.new
  end

  def create 
    @doctor = Doctor.new(doctor_params)
    if @doctor.save
      redirect_to doctors_path
    else
      render :new
    end
  end

  def edit
  end

  def update
    if @doctor.update(doctor_params)
      redirect_to doctors_path
    else
      render :edit
    end
  end

  def destroy
    @doctor.destroy
    redirect_to doctors_path
  end

  private

  def set_doctor
    @doctor = Doctor.find(params[:id])
  end

  def doctor_params
    params.require(:doctor).permit(:name)
  end

end

now we'll do the CRUD for appointments nested inside of doctors
class AppointmentsController < ApplicationController
  before_action :set_doctor 
  before_action :set_appointment, only: [:show, :edit, :update, :destroy]
  def index
    @appointments = @doctor.appointments
  end

  def show
  end

  def new
    @appointment = Appointment.new
  end
  
  def create
    @appointment = @doctor.appointments.new(appointment_params)
    if @appointment.save
      redirect_to doctor_appointments_path(@doctor)
    else
      render :new
    end
  end

  def edit
  end

  def update
    if @appointment.update(appointment_params)
      redirect_to doctor_appointments_path(@doctor)
    else
      render :edit
    end
  end

  def destroy
    @appointment.destroy
    redirect_to doctor_appointments_path
  end

  private

  def set_doctor
    @doctor = Doctor.find(params[:doctor_id])
  end
  
  def set_appointment
    @appointment = Appointment.find(params[:id])
  end

  def appointment_params
    params.require(:appointment).permit(:date, :patient_id)
  end
end

then lastly we will do all the CRUD actions for patients
class PatientsController < ApplicationController
  before_action :set_patient, only: [:show, :edit, :update, :destroy]

  def index
    @patients = Patient.all
  end

  def show
  end

  def new
    @patient = Patient.new
  end

  def create 
    @patient = Patient.new(patient)
    if @patinet 
      redirect_to patients_path
    else
      render :new
    end
  end

  def edit
  end

  def update 
    if @patient.update(patient_params)
      redirect_to patients_path
    else
      render :edit
    end
  end

  def destroy
    @patient.destroy
    redirect_to patients_path
  end

  private

  def set_patient
    @patient = Patient.find(params[:id])
  end

  def patient_params
    params.require(:patient).permit(:name)
  end

end
