# Build an ActionCable Chat Service
15. Generate Job to handle Broadcasts

    ```ruby
    rails g job BroadcastMessage
    ```

16. Add after_create_commit hook to send broadcast job.

    ```ruby
    after_create_commit { BroadcastMessageJob.perform_later self }
    ```
    
    ```bash
    git add .
    git commit -am "Fin"
    ```

17. Restart rails server and demo working ActionCable in browser.

18. Set up devise

    Add to the Gemfile:
    ```ruby
    gem 'devise', github: 'plataformatec/devise'
    ```
    
    Install Devise and Generate User Model
    ```bash
    bundle install
    rails g devise:install
    rails g devise User
    rails g migration AddUserToMessages user:references:index
    rails db:migrate
    git add .
    git commit -am "Devise and User Model"
    ```

19. Add belongs_to to Message Model:

    message.rb:
    ```ruby
    belongs_to :user
    ```
     
20. Update add devise before_action to controller:
  
    rooms_controller.rb:
    ```ruby
    before_action :authenticate_user!
    ```

21. Update v2 files
    
    application.html.erb
    _message.html.erb
    room.coffee
    rooms.coffee
    show.html.erb

22. Explain current_user, warden config. Add warden hooks:

    Populate:
    config/initializers/warden_hooks.rb
    connection.rb

23. Demonstrate in the browser. *RESTART SERVER*

24. v3 STYLE
