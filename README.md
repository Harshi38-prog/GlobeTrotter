import java.util.*;

public class GlobeTrotter {

    public static void main(String[] args) {
        String destination = "Goa";
        int days = 3;
        int totalBudget = 15000;
        String interest = "Beach & Food";

        System.out.println("🌍 GlobeTrotter – Smart Travel Planner\n");

        // Generate smart recommendations
        List<String> places = getRecommendations(interest);

        // Calculate per-day budget
        int perDayBudget = totalBudget / days;

        // Display itinerary
        System.out.println("Destination : " + destination);
        System.out.println("Interest    : " + interest);
        System.out.println("Total Budget: ₹" + totalBudget);
        System.out.println("--------------------------------------");

        for (int i = 0; i < days; i++) {
            String place = places.get(i % places.size());
            System.out.println("Day " + (i + 1) + ": Visit " + place +
                    " | Estimated Cost: ₹" + perDayBudget);
        }

        System.out.println("\n✨ Personalized itinerary generated using intelligent logic!");
    }

    // Rule-based recommendation engine
    public static List<String> getRecommendations(String interest) {
        List<String> list = new ArrayList<>();

        if (interest.equalsIgnoreCase("Beach & Food")) {
            list.add("Baga Beach");
            list.add("Calangute Beach");
            list.add("Local Sea Food Market");
        } else if (interest.equalsIgnoreCase("Nature")) {
            list.add("Waterfalls");
            list.add("Hill View Points");
            list.add("Nature Parks");
        } else {
            list.add("City Attractions");
            list.add("Local Markets");
            list.add("Cultural Spots");
        }
        return list;
    }
}
