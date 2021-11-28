class Ticket {
  status {
    Available {
      sell -> Sold;
      eventPassed -> Expired;
      passBuyingWindow -> Not_Sold;
    }
    Sold {
      eventClose -> Not_Resellable;
      exchange -> Being_Exchanged;
      eventPassed -> Expired;
      noAttendance -> Unused;
    }
    Being_Exchanged {
      noAttendance -> Unused;
      eventPassed -> Expired;
    }
    Not_Resellable {}
    Expired {}
    Unused {}
    // Invalid {}
    Not_Sold {}
  }
}