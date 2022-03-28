# Flour-Pack-Problem

public class Parsing {

    public static void main(String[] args) {
        System.out.println(canPack(20, 10, 59));
    }

    public static boolean canPack(int bigCount, int smallCount, int goal) {
        if (bigCount < 0 || smallCount < 0 || goal < 0) {
            return false;
        }

        int math = bigCount * 5;
        int sum = math;

        if(math > 0 && smallCount >= 0 && goal % 5 == 0){
            sum = sum % 5;
            goal = goal % 5;
            return sum == goal;
        }

        for (int i = 0; i < smallCount; i++) {
            sum = sum + 1;
            if(sum == goal) {
                break;
            }
        }

        int sum2 = 0;
        int newGoal = goal;

        while(sum > goal && smallCount > 0 && goal > 5) {
            sum = sum - 5;
            int goalRemainder = goal - 5;
            goal = goal - 5;
            sum2 = sum2 + 5;

            if(goal == 5 || smallCount >= goalRemainder) {
                sum2 = sum2 + goalRemainder;
                break;
            }
        }
        return sum == goal || sum2 == newGoal;
    }
}

