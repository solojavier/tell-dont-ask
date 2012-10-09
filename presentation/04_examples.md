!SLIDE subsection transition=scrollUp

# Examples

!SLIDE small transition=scrollDown

	@@@ruby
	class Wallet
	  attr_accessor :cash
	end

	class Customer
	  has_one :wallet
	end

	class Paperboy
	  
	  def collect_money(customer, due_amount)
	  
	    if customer.wallet.cash < due_ammount
	      raise InsufficientFundsError
	    else
	      customer.wallet.cash -= due_amount
	      @collected_amount += due_amount
	    end
	  
	  end

	end

!SLIDE small transition=scrollDown

	@@@ruby
	class Wallet
	  attr_accessor :cash

	  def withdraw(amount)
	     raise InsufficientFundsError if amount > cash
	     cash -= amount
	     amount
	  end
	end

	class Customer
	  has_one :wallet

	  def pay(amount)
	    @wallet.withdraw(amount)
	  end
	end

	class Paperboy

	  def collect_money(customer, due_amount)
	    @collected_amount += customer.pay(due_amount)
	  end

	end

!SLIDE small transition=scrollDown

	@@@ruby
	# Not so good
	class Post
	  def send_to_feed
	    if user.is_a?(TwitterUser)
	      user.send_to_feed(contents)
	    end
	  end
	end

	class User
	  def send_to_feed(contents)
	    twitter_client.post_to_feed(contents)
	  end
	end

!SLIDE small transition=scrollDown

	@@@ruby
	# Better
	class Post
	  def send_to_feed
	    user.send_to_feed(contents)
	  end
	end

	class TwitterUser
	  def send_to_feed(contents)
	    twitter_client.post_to_feed(contents)
	  end
	end

	class EmailUser
	  def send_to_feed(contents)
	    # no-op.
	  end
	end