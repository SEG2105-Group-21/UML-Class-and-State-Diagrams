class User {
  name;
  email;
  int phoneNumber;
}

class Artist {
  isA User;
  Performance[] tour;
  1 -- * Performance;
  
  private Performance[] bookTour() {}
}

class Customer {
  isA User;
  int creditCardNumber;
  Order[] bookedEvents;
  1 -- * Order;
  
  private void createOrder() {}
  private void resellTicket() {}
  private void exchangeTicket() {}
}

class Performance {
  date;
  time;
  Venue location;
  1..* -- 1 Venue;
  Artist performer;
}

class Venue {
  name;
  address;
  city;
  int capacity;
  Performance[] events;
  Seat[] allSeats;
  1 <@>- 1..* Seat;
  
  public void verifyArtist() {}
}

class Seat {
  float price;
  int id;
  boolean isOccupied;
}

class Order {
  float price;
  int timeRemaining;
  Performance event;
  1 -> 1 Performance;
  Seat[] tickets;
  1 -> 1..6 Seat;
  
  public boolean verifyCreditCard(int ccNumber) {}
}