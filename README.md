import java.util.*;

public class GlobeTrotter {

    static class Activity {
        String name;
        int cost;

        Activity(String name, int cost) {
            this.name = name;
            this.cost = cost;
        }
    }

    static class CityStop {
        String cityName;
        List<Activity> activities = new ArrayList<>();

        CityStop(String cityName) {
            this.cityName = cityName;
        }

        void addActivity(String name, int cost) {
            activities.add(new Activity(name, cost));
        }

        int getCityCost() {
            int sum = 0;
            for (Activity a : activities) {
                sum += a.cost;
            }
            return sum;
        }
    }

    static class Trip {
        String tripName;
        List<CityStop> stops = new ArrayList<>();

        Trip(String tripName) {
            this.tripName = tripName;
        }

        void addCity(String cityName) {
            stops.add(new CityStop(cityName));
        }

        int getTotalCost() {
            int total = 0;
            for (CityStop stop : stops) {
                total += stop.getCityCost();
            }
            return total;
        }

        void displayItinerary() {
            System.out.println("\nTrip: " + tripName);
            for (CityStop stop : stops) {
                System.out.println("City: " + stop.cityName);
                for (Activity a : stop.activities) {
                    System.out.println("   - " + a.name + " : ₹" + a.cost);
                }
                System.out.println("   City Cost: ₹" + stop.getCityCost());
            }
            System.out.println("\nTotal Trip Cost: ₹" + getTotalCost());
        }
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter Trip Name: ");
        String tripName = sc.nextLine();
        Trip trip = new Trip(tripName);

        System.out.print("Number of Cities: ");
        int cityCount = sc.nextInt();
        sc.nextLine();

        for (int i = 0; i < cityCount; i++) {
            System.out.print("\nEnter City Name: ");
            String cityName = sc.nextLine();
            CityStop stop = new CityStop(cityName);

            System.out.print("Number of Activities in " + cityName + ": ");
            int activityCount = sc.nextInt();
            sc.nextLine();

            for (int j = 0; j < activityCount; j++) {
                System.out.print("Activity Name: ");
                String activityName = sc.nextLine();

                System.out.print("Activity Cost: ");
                int cost = sc.nextInt();
                sc.nextLine();

                stop.addActivity(activityName, cost);
            }
            trip.stops.add(stop);
        }

        trip.displayItinerary();
        sc.close();
    }
}

